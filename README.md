# Access Token Generator for Mastodon API

***Currently all translastions are provided by Google Translate. A
revised README is coming.***

* https://takahashim.github.io/mastodon-access-token/

Mastodon APIを叩くにはaccess_tokenが必要ですが、現状Mastodonの設定画面では直接取得するUIがないため、外部から取得するためのSPA(Single Page Application)サイトを作りました。
実験用にaccess tokenが必要な際などにお使いください（もっとも第三者も利用する本格的なアプリケーションを作るのであればこのような仕組みをアプリ自体で実装するべきなので、あくまで実験用のものとお考えください）。

Access_token is required to hit Mastodon API, but since there is no UI
to acquire directly on the current setting screen of Mastodon, we
created a SPA (Single Page Application) site to acquire from outside.
Please use it when you need an access token for experimentation, etc. 
(If you want to make a full-scale application that even third parties
use, such a mechanism should be implemented by the application itself,
so it should be used only for experimentation. Please think).

## 使い方 (Usage)

「Mastodon URL」には使っているMastodonインスタンスのURLを、「Client Name」には設定画面で表示させたいアプリケーション名を、「Web site」にはWebサイト名を、それぞれ入力してください。
「Publish access_token」ボタンを押し、Mastodonインスタンス側で認証処理を正常に実行されると、access_token（とclient_id、client_secret）が表示されます。

For "Mastodon URL", enter the URL of the Mastodon instance you are
using, for "Client Name", enter the name of the application you want to
display on the settings screen, and for "Web site", enter the name of
the website. Press the “Publish accesstoken” button and authenticate on
the Mastodon instance side.

## セキュリティ (Security)

仕組みの都合で、どうしてもMastodonインスタンスのアクセス情報（client_id, client_secret, access_token）を取得する必要があります。

外部サイト上で秘密情報を扱うのは望ましくない方法なのですが、それでも安全性を極力担保するべく、サイトの挙動の透明性を高めてみました。JavaScriptも[Vanilla JS](http://vanilla-js.com/)で記述し、index.html内で完結させています。JavaScriptからサーバには一切アクセスしません（そもそもGitHub Pagesなのでサーバ側にアプリを仕掛けたりとかもできませんし、外部のJavaScriptも読み込まないようにしています）。ページ遷移間で情報の引き渡しにはクッキー等は使わず、localStorageに保存しています。
jQuery等を使った方がコードは簡潔になりそうですが、透明性を優先しました（そのためGoogle Analyticsとかも入れてないのでアクセス数もよく分からず……。）


なおCSSには[Bulma](http://bulma.io/)と[Font Awesome](http://fontawesome.io/)を使っています（publicなCDN経由なので変なものは仕込めません）。BulmaはJavaScript不要で使える軽量CSSフレームワークで便利です。

Due to the mechanism, it is absolutely necessary to obtain access
information (clientid, clientsecret, access_token) of Mastodon instance.

Although it is an undesirable way to handle confidential information on
an external site, I tried to increase the transparency of the behavior
of the site in order to assure security as much as possible. JavaScript
is also written in Vanilla JS and completed in index.html. The server is
not accessed from JavaScript at all (in the first place, since it is
GitHub Pages, it is not possible to set up an application on the server
side, so that external JavaScript is not loaded). Cookies are not used
to pass information between page transitions, but are stored in
localStorage. The code seems to be simpler if you use jQuery etc., but
priority was given to transparency (so Google Analytics is not included,
so the number of accesses is not well known ...)

In addition, we use Bulma and Font Awesome for CSS (you can't put
something strange because it is via public CDN). Bulma is a lightweight
CSS framework that can be used without JavaScript.

## 作者 (Author)

[@takahashim](https://mstdn.jp/takahashim)
