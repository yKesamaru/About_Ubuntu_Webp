# 結論
以下を実行。
```bash
sudo add-apt-repository ppa:krifa75/eog-ordissimo; sudo apt update && sudo apt install webp-pixbuf-loader -y
```
以上。
# 従来の方法
- [Ubuntu 20.04 LTSでHEIFとWebPを扱う](https://mackro.blog.jp/archives/6545568.html)[ファイラーでWebPのサムネイルを表示する]
  - 変換(dwebp)を挟む
  - 設定ファイルを書く
# なぜ共有するのか
- ファイラにWebPファイルのサムネイルが正しく表示されない状態がUbuntu18.04および20.04において未だに(2022年1月現在)存在している
- 調査に時間を使った
- 同じ内容の日本語の情報がなかった
- 従来の方法は手間が多い

# Reference
- [How to Use WebP Images in Ubuntu and Other Linux Distributions: It's FOSS](https://itsfoss.com/webp-ubuntu-linux/)
- [How to Enable Thumbnails for WebP Files in Ubuntu 20.04 / Fedora 34: FOSTips](https://fostips.com/enable-thumbnails-webp-ubuntu-fedora/)
- [EogOrdissimo: Launchpad](https://launchpad.net/~krifa75/+archive/ubuntu/eog-ordissimo)
- 補足
  - [webp-pixbuf-loader 0.0.3-1: ArchLinux](https://www.archlinux.jp/packages/community/x86_64/webp-pixbuf-loader/)
  - [webp-pixbuf-loader-0.0.2-2.fc34.x86_64.rpm: Fedora](https://fedora.pkgs.org/34/fedora-x86_64/webp-pixbuf-loader-0.0.2-2.fc34.x86_64.rpm.html)
  - [ダウンロード: Package list krifa](https://launchpad.net/~krifa75/+archive/ubuntu/eog-ordissimo/+packages)

# 検証環境
- ファイラ
  - GNOME nautilus 3.26.4
  - Thunar 1.6.15 (Xfce 4.12)
  - pcmanfm 1.2.5  
- インストール済ライブラリ
  - libwebp6 0.6.1-2ubuntu0.18.04.1
  - libwebp6:i386 0.6.1-2ubuntu0.18.04.1
  - libwebpdemux2 0.6.1-2ubuntu0.18.04.1
  - libwebpmux3 0.6.1-2ubuntu0.18.04.1

# 検証
## 実行前
![nautilus](https://raw.githubusercontent.com/yKesamaru/About_Ubuntu_Webp/master/img/_nautilus.png)*GNOME nautilus 3.26.4*  
![thunar](https://raw.githubusercontent.com/yKesamaru/About_Ubuntu_Webp/master/img/_thunar.png)*Thunar 1.6.15*  
![pcmanfm](https://raw.githubusercontent.com/yKesamaru/About_Ubuntu_Webp/master/img/_pcmanfm.png)*pcmanfm 1.2.5*  

```bash
sudo add-apt-repository ppa:krifa75/eog-ordissimo; sudo apt update && sudo apt install webp-pixbuf-loader -y
(省略)
以下のパッケージが新たにインストールされます:
  webp-pixbuf-loader
アップグレード: 0 個、新規インストール: 1 個、削除: 0 個、保留: 15 個。
6,516 B のアーカイブを取得する必要があります。
この操作後に追加で 28.7 kB のディスク容量が消費されます。
取得:1 http://ppa.launchpad.net/krifa75/eog-ordissimo/ubuntu bionic/main amd64 webp-pixbuf-loader amd64 0.2.1-bionic1 [6,516 B]
6,516 B を 1秒 で取得しました (12.8 kB/s)     
以前に未選択のパッケージ webp-pixbuf-loader を選択しています。
(データベースを読み込んでいます ... 現在 400423 個のファイルとディレクトリがインストールされています。)
.../webp-pixbuf-loader_0.2.1-bionic1_amd64.deb を展開する準備をしています ...
webp-pixbuf-loader (0.2.1-bionic1) を展開しています...
webp-pixbuf-loader (0.2.1-bionic1) を設定しています ...
libgdk-pixbuf2.0-0:amd64 (2.36.11-2) のトリガを処理しています ...
```
## 実行後
![nautilus](https://raw.githubusercontent.com/yKesamaru/About_Ubuntu_Webp/master/img/shadow_nautilus_after.png)*GNOME nautilus 3.26.4*  
![thunar](https://raw.githubusercontent.com/yKesamaru/About_Ubuntu_Webp/master/img/shadow_thunar_after.png)*Thunar 1.6.15*  
![pcmanfm](https://raw.githubusercontent.com/yKesamaru/About_Ubuntu_Webp/master/img/shadow_pcmanfm_after.png)*pcmanfm 1.2.5*  
# 備考
- Fedora, Arch, Manjaro^[未確認], openSUSE(Tumbleweed)^[未確認]では公式リポジトリから提供(2022年1月現在)
- [How to Enable Thumbnails for WebP Files in Ubuntu 20.04 / Fedora 34: FOSTips](https://fostips.com/enable-thumbnails-webp-ubuntu-fedora/)ではインストール後に`ppaの削除`を推奨している
  - 理由: EOGに不具合が出る可能性があるから^[未確認]
- `pcmanfm`で特定ファイルだけサムネイルが表示されない