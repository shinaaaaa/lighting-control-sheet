# 概要
Sync Lightime(仮称、作成予定)向けのライティングコントロール用のフォーマットです  
cue シートみたいな感じです  

# 書式
```
# メタデータ
TITLE "タイトル"
URL "https://example.com"
COMP_DEVICES "device_1", "device_2"
DESCRIPTION "説明"

# ライティングコントロール
TIME HH:mm:ss.ffffff
 メソッド
```
- 拡張子は **.slst** です
- メタデータの部分にはタイトル、配信先URL、ファイルの説明を記入します
- ライティングのコントロールの部分には時間の指定と、色、輝度、光り方などの指定をします

<details>
<summary>メタデータ</summary>
  
- TITLE "タイトル"
    - シートのタイトルです
- URL "https://example.com"  
    - 配信等の場合のURLです
- COMP_DEVICES "デバイス名_1", "デバイス名_2" ...  
    - 作者が確認済みのデバイス一覧
- DESCRIPTION "説明"  
    - ファイルの説明です
</details>

<details>
<summary>ライティングコントロール</summary>

- TIME HH:mm:ss.fffff
    - 時間をミリ秒まで指定します
    - この行の下にメソッドを記入します

#### メソッド
- COLOR red green blue alpha
  - ライトの色と輝度の設定
  - red, green, blueは0から255の整数で色を指定していします
  - alphaは0から1の少数で輝度を指定します
- ON
  - ライトを点灯させます
  - 色は最後に指定した色になります
- OFF
  - ライトを消灯させます
- FLASH interval
  - ライトを点滅させます
  - intervalはミリ秒で点滅の間隔を指定します

</details>

# サンプル
```
TIME 00:00:00.000000
 COLOR 0 0 255 0.5

TIME 00:00:03.000000
 COLOR 0 255 0 0.8
 FLASH 100

TIME 00:00:05.500000
　OFF

TIME 00:00:06.000000
 COLOR 255 0 255 1
 ON
```

# 更新履歴
2023-08-01 alpha 0.1
- 🎉フォーマットの定義を開始しました🎉
- 書式の作成
- メソッドの定義(COLOR, ON, OFF, FLASH)

2023-08-01 alpha 0.2
- 少し表記を変えました