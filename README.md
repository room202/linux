# Linux

## 使用するテキスト

[新しいLinuxの教科書 第2版](https://www.sbcr.jp/product/4815624316/)

## 開発環境

- VirtualBox
  - OS : CentOS Stream 9
- Tera Term

## 開発環境の構築手順

###  VirtualBoxインストール

[こちらを参照](https://github.com/room202/vbox)

### VirtualBox に CentOS Stream 9をインストール

[こちらを参照](https://github.com/room202/vbox-centos9)

### TeraTermインストール

[こちらを参照](https://github.com/room202/teraterm)

### CentOS Stream 9 での LAMP環境構築

※これは任意です。

[こちらを参照](https://github.com/room202/centos9-lamp)

# 新しいLinuxの教科書 第2版

## Chapter01 : Linuxを使ってみよう

### 01 Linuxとは
### 02 Linux環境を用意する
### 03 ログイン、ログアウト、シャットダウン

## Chapter02 : シェルって何だろう？

### 01 シェルとコマンド
### 02 プロンプト
### 03 シェルの種類
### 04 どのシェルを選ぶか
### 05 ターミナルとは

## Chapter03 : シェルの便利な機能

### 01 コマンドラインの編集

| 内容 | コマンド |
| ---- | ---- |
| 後に1文字移動(Back) | Ctrl + b |
| 前に1文字移動(Forward) | Ctrl + f |
| 行頭に移動 | Ctrl + a |
| 行末に移動 | Ctrl + e |
| 後方に単語1つぶん移動 | Meta(ESC or Alt) + b |
| 前方に単語1つぶん移動 | Meta(ESC or Alt) + f |
| カーソル位置の後方に1文字削除 | BSキー or Ctrl + h |
| カーソル位置の1文字削除 | Delキー or Ctrl + d |
| 後方にスペース区切りで1単語ぶん削除 | Ctrl + w |
| カーソル位置から行末までを削除する | Ctrl + k |
| カーソル位置から行頭までを削除する | Ctrl + u |
| 最後に削除した内容を挿入する | Ctrl + y |

### 02 トラブル時には

| 内容 | コマンド |
| ---- | ---- |
| 画面表示ロック | Ctrl + s |
| 画面表示ロック解除 | Ctrl + q |
| 実行中のコマンドを強制終了 | Ctrl + c |
| 画面クリア | Ctrl + l (エル) |
|  |  |

### 03 補完機能

- TABキーで補完機能が作動する

### 04 コマンド履歴

| 内容 | コマンド |
| ---- | ---- |
| 1つ前のコマンド履歴に移動 | Ctrl + p or ↑キー |
| 次のコマンド履歴へ移動 | Ctrl + n or ↓キー |
| 履歴を遡ってインクリメンタル検索する | Ctrl + r |

#### インクリメンタル検索時の操作

| 内容 | コマンド |
| ---- | ---- |
| 検索語を追加して再検索 | (文字の入力) |
| 1つ前の検索結果へ移動 | Ctrl + r |
| Enterキー | 現在の検索結果をそのまま実行 |
| ESCキー | 現在の検索結果を表示したまま、コマンドラインに戻る |
| 検索結果を破棄し、プロンプトに戻る | Ctrl + g |
|  |  |

## Chapter04 : ファイルとディレクトリ

### 01 Linuxはファイルからできている
### 02 Linuxのディレクトリ構造
### 03 絶対パスと相対パス
### 04 ディレクトリの移動
### 05 lsコマンド

```bash
ls
ls -a
ls -l
ls -F
ls -aF
ls -al
ll
```

| 種類 | 記号 |
| ---- | ---- |
| 通常ファイル | なし |
| ディレクトリ | / |
| 実行可能ファイル | * |
| シンボリックリンク | @ |
|  |  |

### 06 コマンドのオプションについて

```bash
ls --quote-name
```

## Chapter05 : ファイル操作の基本

### 01 mkdirコマンド

```bash
mkdir dir1
mkdir -p dir1/dir2/dir3
```

### 02 touchコマンド

```bash
touch filename1
touch filename2 filename3
```

### 03 rmとrmdirコマンド

```bash
rm filename
rm -r dir1
rmdir dir1
```

### 04 catコマンド

```bash
cat /etc/bashrc
cat -n /etc/bashrc
cat /etc/bashrc ~/.bashrc
```

### 05 lessコマンド

```bash
less /etc/bashrc
```

| 内容 | コマンド |
| ---- | ---- |
| 1画面下にスクロールする | スペースキー、f、Ctrl + v |
| 1画面上にスクロールする | b、Meta + v |
| 1行下にスクロールする | j、Ctrl + n、Enterキー |
| 1行上にスクロールする | k、Ctrl + p |
| lessコマンドを終了する | q |
| 下方向に向かって内検索 | /キーワード |
| 上方向に向かって内検索 | ?キーワード |
| 次の検索結果に移動する | n |
| 前の検索結果に移動する | Shift + n |
| ヘルプ画面の表示 | h |
| ヘルプ画面を閉じる | q |

### 06 cpコマンド

```bash
cp file1 file2
```

### 07 mvコマンド

```bash
mv file1 file2
```

### 08 lnコマンド

```bash
# ハードリンク
ln file1 file2

# シンボリックリンク
ln -s file1 file2
```

## Chapter 06 探す、調べる

### 01 ファイルを探す

#### findコマンド

```bash
find . -name file-1.txt
find . -name '*.html'
find . -name '*.html' -type d
```
- ファイル種別を-typeで指定

| ファイル種別 | 指定 |
| ---- | ---- |
| 通常ファイル | -type f |
| ディレクトリ | -type d |
| シンボリックリンク | -type l |

#### locateコマンド

```bash
# Redhat系
dnf install mlocate

# Debian
apt install plocate

# ファイルデータベース更新
updatedb

locate bash
locate '*.sed'
```

### 02 コマンドの使い方を調べる

```bash
# --help
cat --help

# manコマンド
man cat
man man
```

### 03 コマンドを探す

```bash
which cat
which -a ping
```

### 04 日本語ドキュメントと英語ドキュメント

## Chapter 07 テキストエディタ

### 01 テキストファイルとバイナリファイル

### 02 Vim

```bash
# Redhat系
dnf install vim

# Debian
dnf install vim

vim --version
```

### 03 ファイルを開く／保存する

```bash
vim newfile1
```

| 内容 | コマンド |
| ---- | ---- |
| :q | Vimを終了する |
| :w | ファイルを上書き保存する |
| :w <ファイル名> | 名前を付けて保存する |
| :q! | ファイルを保存せずにVimを終了する |
| h | 左に移動する |
| j | 下に移動する |
| k | 上に移動する |
| l | 右に移動する |
| x | カーソル位置の文字を削除する |
| i | カーソル位置の左に文字を追加する |
| a | カーソル位置の右に文字を追加する |
| w | 前方に単語１つぶん移動する |
| b | 後方に単語１つぶん移動する |
| W | スペース区切りで前方に単語１つぶん移動する |
| B | スペース区切りで後方に単語１つぶん移動する |
| 0 | 行頭に移動する |
| $ | 行末に移動する |
| gg | 1行目に移動する |
| Ｇ | 最後の行に移動する |
| <数字>G | <数字>行目に移動する |
| d$ | 行末までデリート |
| d0 | 行頭までをデリート |
| x、dl | 1文字をデリート |
| dw | 単語１つをデリート |
| dgg | 最初の行までをデリート |
| dG | 最後の行までをデリート |
| p | 貼り付け |
| yy | 現在カーソルのある行をヤンク(コピー) |
| dd | 現在カーソルのある行をデリート |
|  |  |
|  |  |
|  |  |
|  |  |
