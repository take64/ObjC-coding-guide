# Objective-Cコーディングスタイルガイド

このコーディングスタイルガイドは同人サークル[besidesplus](http://besidesplus.net/)のiOSアプリ開発用コーディング規約です。


## はじめに

この規約は所謂modern Objective-Cと呼ばれる記法と異なる部分が多々あります。


## 目次

* [インデント](#インデント)
* [スペーシング](#スペーシング)


## インデント

* インデントにはスペース４つを利用する。タブを使ったインデントは利用しない。
> "これは開発環境の変化、及び参照時の崩れを防ぐ為である。"


## スペーシング

* 変数の桁合わせのスペーシングには[インデント](#インデント)と同じくスペース4つを利用する。
* 型の位置と変数の位置、=の位置を合わせる。

** Good **
```objc
floot   any  = 1.0f;
int     some = 2;
```

** Bad **
```objc
floot any = 1.0f;
int some = 2;
```
> ※ただし変数定義が並ばない場合はこの限りではない
> ```objc
floot any = 1.0f;
```

## ドット記法構文

* ドット記法構文は構文のパターンによって__メッセージ式__と__ドット記法__使い分ける

** ドット記法を利用する場合 **

```objc
// block構文
self.completeBlock(userInfo,error);

// 構造体利用
CGFlot width = frame.size.width;
```

** メッセージ式を利用する場合( Good ) **
```objc
// プロパティ取得
UIColor *color = [[self view] backgroundColor];

// プロパティ設定
[[self view] setBackgroundColor:[UIColor blueColor]];
```

** メッセージ式を利用する場合( Bad ) **
```objc
// プロパティ取得
UIColor *color = self.view.backgroundColor;

// プロパティ設定
self.view.backgroundColor = [UIColor blueColor];
```
> これは、ドット記法で得られたプロパティに対してメッセージ式を投げ込むという矛盾を改善する為です。

> ※一般的にmodern Objective-Cではなるべくドット記法を利用するべきとなっていますが、上記の矛盾を解決できる術がないうちはおいそれとドット記法を導入するべきではありません。(ドット記法を利用するのであればSwiftに移行した方が易いでしょう)
