# Access Token Generator for Mastodon API

* https://takahashim.github.io/mastodon-access-token/

Mastodon APIを叩くにはaccess_tokenが必要ですが、現状Mastodonの設定画面では直接取得するUIがないため、外部から取得するためのSPA(Single Page Application)サイトを作りました。
実験用にaccess tokenが必要な際などにお使いください（もっとも第三者も利用する本格的なアプリケーションを作るのであればこのような仕組みをアプリ自体で実装するべきなので、あくまで実験用のものとお考えください）。

## 使い方 (Usage)

「Mastodon URL」には使っているMastodonインスタンスのURLを、「Client Name」には設定画面で表示させたいアプリケーション名を、「Web site」にはWebサイト名を、それぞれ入力してください。
「Publish access_token」ボタンを押し、Mastodonインスタンス側で認証処理を正常に実行されると、access_token（とclient_id、client_secret）が表示されます。

## セキュリティについて (Security)

仕組みの都合で、どうしてもMastodonインスタンスのアクセス情報（client_id, client_secret, access_token）を取得する必要があります。

外部サイト上で秘密情報を扱うのは望ましくない方法なのですが、それでも安全性を極力担保するべく、サイトの挙動の透明性を高めてみました。JavaScriptも[Vanilla JS](http://vanilla-js.com/)で記述し、index.html内で完結させています。JavaScriptからサーバには一切アクセスしません（そもそもGitHub Pagesなのでサーバ側にアプリを仕掛けたりとかもできませんし、外部のJavaScriptも読み込まないようにしています）。ページ遷移間で情報の引き渡しにはクッキー等は使わず、localStorageに保存しています。
jQuery等を使った方がコードは簡潔になりそうですが、透明性を優先しました（そのためGoogle Analyticsとかも入れてないのでアクセス数もよく分からず……。）


なおCSSには[Bulma](http://bulma.io/)と[Font Awesome](http://fontawesome.io/)を使っています（publicなCDN経由なので変なものは仕込めません）。BulmaはJavaScript不要で使える軽量CSSフレームワークで便利です。

## 作者 (Author)

[@takahashim](https://mstdn.jp/takahashim)
