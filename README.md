# 【第2回】フレームワークを使ったプログラミング
## テーマ
1. フレームワークを使ったプログラムを体験してみよう
2. GETパラメータの取得

## 開発環境について
* この演習では、Codespacesと呼ばれるサービスを使って開発を行います。
* ブラウザ上で動作する開発環境です、インストール不要で使う事ができます。

## Codespacesで実行してみよう
* 第一回で実施した[手順](/Codespacesの実行手順.md)を参照してください。

## フレームワークを使ったGETパラメータの取得方法について学習
1. `Let's try!`を押します。
![image](https://user-images.githubusercontent.com/32722128/151342462-816a78b1-68cc-4a12-a2cc-4156b34ac711.png)

2. 機能の説明が記載されていることを確認しましょう。
![image](https://user-images.githubusercontent.com/32722128/151342667-836c8ba8-dbf0-4cbe-9469-478848c13233.png)

3. アドレスバーの最後に「/morning?name=名前」と追記してください、「名前」の部分は自分の苗字に変更しましょう。
![image](https://user-images.githubusercontent.com/32722128/151343167-79342186-8cf8-4c28-9336-785926da8c1d.png)

4. 「○○さん、おはようございます!」と表示される事を確認しましょう。
![image](https://user-images.githubusercontent.com/32722128/151343551-f48b1629-4629-421e-b554-a475d94a36d7.png)

5. 確認が終わったら、タブを閉じましょう
![image](https://user-images.githubusercontent.com/32722128/150733257-a1056c19-1b24-412b-8bfc-a6063e75c785.png)

6. デバック実行中ですので、停止ボタンを押して、デバック実行を停止しましょう。
![image](https://user-images.githubusercontent.com/32722128/150748527-d7121765-5142-4f5a-9769-33c0c23627a4.png)

## 解説 GETパラメータの取得
* GETパラメータは別名、URLパラメータとも呼ばれます、URLの末尾に特定の形式で文字列を追加し、リクエストを送信すると、WEBアプリケーションへ値を渡すことが出来ます。  
* URLの末尾に「?」クエスチョンマークを付けて、「?パラメータ名1=値1&パラメータ名2=値2」の形式で記載します。

* 例えば、Googleで「GETパラメータ」と検索すると、以下のようなURLへ移動します。
`https://www.google.com/search?q=GETパラメータ&sxsrf=AOaemvLICEhVFXxVR6bxxZU-h_bfqkZGaw%3A1643282358884&ei=tn_yYcWyNdn8wAOTop6YDA&ved=0ahUKEwjF5ZDq59H1AhVZPnAKHRORB8MQ4dUDCA4&uact=5&oq=GET%E3%83%91%E3%83%A9%E3%83%A1%E3%83%BC%E3%82%BF&gs_lcp=Cgdnd3Mtd2l6EAMyBwgjELADECcyBwgAEEcQsAMyBwgAEEcQsAMyBwgAEEcQsANKBQg8EgExSgQIQRgASgQIRhgAUABYAGCrEWgBcAJ4AIABAIgBAJIBAJgBAMgBBMABAQ&sclient=gws-wiz`

* このうち
`?q=GETパラメータ&sxsrf=AOaemvLICEhVFXxVR6bxxZU-h_bfqkZGaw%3A1643282358884&ei=tn_yYcWyNdn8wAOTop6YDA&ved=0ahUKEwjF5ZDq59H1AhVZPnAKHRORB8MQ4dUDCA4&uact=5&oq=GET%E3%83%91%E3%83%A9%E3%83%A1%E3%83%BC%E3%82%BF&gs_lcp=Cgdnd3Mtd2l6EAMyBwgjELADECcyBwgAEEcQsAMyBwgAEEcQsAMyBwgAEEcQsANKBQg8EgExSgQIQRgASgQIRhgAUABYAGCrEWgBcAJ4AIABAIgBAJIBAJgBAMgBBMABAQ&sclient=gws-wiz`
の部分がGETパラメータにあたります。

* 先ほどの「動かしてみよう」では、URLの末尾に`/morning?name=名前`と追記してページ移動を行いました。
* この時、パラメータ名は`name`で、値は`名前`でGETリクエストが送信されました。
`/step2/morning`とPATH指定されてましたので、`Step2Controller`クラスの`morning`メソッドでリクエストが処理されます。
これは`@RequestMapping`、`@GetMapping`というアノテーションでそう指定されているためです。
![image](https://user-images.githubusercontent.com/32722128/151350907-6260c4c8-a736-4a5f-a1c6-dea17eaa2913.png)

* また、`@RequestParam`アノテーションでどのパラメータ名で渡されたGETパラメータをどの引数に代入するかを指定しています。
* `name`というパラメータ名でリクエストされた値を、`name`というメソッド引数に代入するよう指定し、パラメータが指定されない事を許容するよう、`required = false`という指定がされています。
![image](https://user-images.githubusercontent.com/32722128/151352160-7906988c-e885-4c72-9022-02055e2008d2.png)

* 受け取った名前と、あいさつの文字列を結合し、addAttributeメソッドを使用して、Thymeleaf(タイムリーフ)に対し値を渡しHTMLを生成しリクエスト元に応答します、HTMLを受け取ったブラウザが画面を行っています。
![image](https://user-images.githubusercontent.com/32722128/151352453-e2ff70b6-66b3-48b4-bc88-10c61db282bb.png)

## 演習level1 step2
### 夜の挨拶を返す処理を追加しましょう。
1. STEP-2のページを開きます。
![image](https://user-images.githubusercontent.com/32722128/151342667-836c8ba8-dbf0-4cbe-9469-478848c13233.png)

2. アドレスバーの最後に「/evening?name=名前」と追記してください、「名前」の部分は自分の苗字に変更しましょう。
![image](https://user-images.githubusercontent.com/32722128/151344209-3195a9dd-42cf-4c9e-817b-0d81a7814a76.png)

3. 「○○さん、こんばんは!」と表示されるように処理を追加してください。
![image](https://user-images.githubusercontent.com/32722128/151344464-344a3229-3e0c-492c-913d-a787baee998a.png)

## ヒント
* `~/src/main/java/com/classroom/assignment/controller/Step2Controller.java`ファイルを書き換えてみましょう。

1. 赤枠の部分を編集しましょう。
![image](https://user-images.githubusercontent.com/32722128/151354680-6f90afcb-3dc6-41cf-a5c7-23319a98d40b.png)

2. 動作確認をしましょう、虫と再生ボタンのアイコンを押します。
![image](https://user-images.githubusercontent.com/93235101/149875480-b6d0189c-52f3-45dd-bcc3-335bff5d76d0.png)

3. `Launch AssignmentApplication`が選択されていることを確認し再生ボタンを押します。
* 初回はダイアログが表示されます、YESを選択してください。
![image](https://user-images.githubusercontent.com/93235101/149875513-ded6ea34-792e-40da-927e-215d7e22bbf2.png)

4. `Open in Browser`を押します。
![image](https://user-images.githubusercontent.com/93235101/149875545-6689fe73-7a32-4be8-8658-eaf8c8ddd460.png)

5. `Let's try!`を押します。
![image](https://user-images.githubusercontent.com/32722128/151342462-816a78b1-68cc-4a12-a2cc-4156b34ac711.png)

6. アドレスバーの最後に「/evening?name=名前」と追記してください、「名前」の部分は自分の苗字に変更しましょう。
![image](https://user-images.githubusercontent.com/32722128/151344209-3195a9dd-42cf-4c9e-817b-0d81a7814a76.png)

7. 「○○さん、こんばんは!」と表示されるように処理を追加してください。
![image](https://user-images.githubusercontent.com/32722128/151344464-344a3229-3e0c-492c-913d-a787baee998a.png)

8. 確認が終わったら、タブを閉じましょう
![image](https://user-images.githubusercontent.com/32722128/150733257-a1056c19-1b24-412b-8bfc-a6063e75c785.png)

9. デバック実行中ですので、停止ボタンを押して、デバック実行を停止しましょう。
![image](https://user-images.githubusercontent.com/32722128/150748527-d7121765-5142-4f5a-9769-33c0c23627a4.png)

## テスト
* 課題の提出前に回答が正しいかテストしてみましょう。
1. `~/src/test/java/com/classroom/assignment/controller/api/Step2ControllerTests.java`を開きます。
![image](https://user-images.githubusercontent.com/32722128/151347158-16e01cc1-17f1-4acd-acf1-3248be222b15.png)

2. shouldReturnDefaultMessagメソッド前の再生ボタンをクリックします。(画面コピーは一度テスト実施済みのためチェックマークに変わっています。)
![image](https://user-images.githubusercontent.com/32722128/151347095-dec8953f-68f5-4628-9ad6-346d9b5054a3.png)

3. 再生ボタンがチェックマークに変わればテスト成功です！
![image](https://user-images.githubusercontent.com/32722128/151347373-51bbd4e8-bc68-4009-8b8c-0aaba13508df.png)

## 課題の提出
* 課題の提出は第一回と同じ[操作](/課題の提出手順.md)のコミット・プッシュ・プルリクエストを実施しましょう。

