# MAIGIFU RP2040 Pico-Like Board ラズパイピコ互換ボード #まいぎふ 
## はじめに
Mouser Make Awards 2024で最優秀賞を受賞して3万円分の電子部品をゲットしたのですが、みんなで楽しめる方法を考えてマイコンボードを設計製作して配ることにしました。マイコンボードを岐阜でギフト＝ #まいぎふ として設計を進める中で、JLCPCBの運営するOSHWLabがプロジェクト趣旨に賛同してくれて、プリント基板製造を支援してくれることになりました。  
#まいぎふ マイコンボードで、電子工作初心者から上級者までみなさんに、もっと気軽に電子工作を楽しんでいただけるとうれしいです。  
## 特徴・仕様
RP2040を搭載して、様々な開発環境に対応してしています。
- C/C++
- Arduino IDE
- MicroPython
- CircuitPython(初期ファームウェア)
- TinyGo

Raspberry Pi Picoに似せたピンアサインですが、一部異なります。  
カラーシルク基板に搭載して、ピンアサインが分かりやすいです。  
たくさん配布するためにコストダウンを行っています。  
- USB Type-Cコネクタ
- セラミック発振子
- 電源用MLCCを省略
- USBデータ線のダンピング抵抗を省略
このマイコンボードの動作や性能に不満を感じた際は、市販のマイコンボードのご購入をお願いします。

## 仕様
- マイコン：RP2040
- フラッシュメモリ：2MB（外付け）
- GPIOピン：26ピン
- インターフェース：USB、I2C、SPI、UART
- Raspberry Pi Picoの3.3ENとAGNDは省略しており機能はありません
- Raspberry Pi PicoにはないRUNボタンを搭載しておりリセット作業が簡単です

## クイックスタートガイド (MicroPython)
(1) 必要なもの
- #まいぎふ マイコンボード
- USBケーブル（データ転送対応）
- 開発PC（Windows, macOS, Linux 対応）

(2) MicroPythonのインストール
- Raspberry Pi PicoのMicroPythonファームウェア(.UF2ファイル)をダウンロード
- BOOTボタンを押しながらRUNボタンを押して放す
- RPI-RP2ドライブが表示されたら、ダウンロードしたファームウェアをドラッグ&ドロップ

(3) 開発環境(Thonny)のセットアップ
- Thonnyの公式サイトからインストーラをダウンロード
- インストーラを実行し、デフォルト設定でインストール
- 初回起動時の言語設定で「日本語」を選択
- 画面右下で「MicroPython (Raspberry Pi Pico) Board CDC @ COM■」(COM番号は使用環境に依存します)
- 新規ファイルを立ち上げ、下記のコードをボード内に"code.py"として保存してください。  

~~~ 
import machine
import time

led = machine.Pin(25, machine.Pin.OUT)

while True:
    led.toggle()  # LEDの状態を反転
    time.sleep(1)  # 1秒待機
~~~

- 現在のスクリプトを実行(F5)ボタンを押すと、ボード上のオレンジLEDが点滅します。


## 関連情報
### ハードウェア
- 部品表(BOM) :マウザーのサイトで基板1枚分のBOMを公開しており、何枚分という形で簡単に一括購入できます  
https://www.mouser.jp/ProjectManager/ProjectDetail.aspx?AccessID=7532113fa2

- 回路図・基板設計情報 : OSHWLabで公開しています。データをブラウザ上で動く回路基板CAD「EasyEDA」に取り込んで、改変、JLCPCBにプリント基板発注も可能です  
https://oshwlab.com/suzan_works/rp2040_pico-compatible_maigifu_2

### ソフトウェア
- C/C++ (Raspberry Pi 公式)
https://www.raspberrypi.com/documentation/microcontrollers/

- CircuitPython  
https://circuitpython.org/board/raspberry_pi_pico/

- Arduino  
https://github.com/earlephilhower/arduino-pico

### 設計ストーリー
- プロトペディアにまとめています  
https://protopedia.net/prototype/6146