# 朗讀反紅（readkaraoke）：原始檔

網站用到 repo 根目錄的 `index.html` 和 `opencc-cn2t.js`（簡→繁字典，按「轉成繁體」時才載入）。
這個資料夾放產生 `index.html` 的原始檔；讀音引擎、GoodTeacher 規則和「漢字加拼音」（messagewithpinyin）共用同一套。

| 檔案 | 用途 |
| --- | --- |
| `template.html` | 畫面、分詞、時間表、播放（逐詞反紅、倒數、捲動） |
| `engine.js` | 讀音判斷、拼音轉注音（從 messagewithpinyin 複製） |
| `gt-rules.json`, `convert_rules.py` | GoodTeacher 語境規則與轉換程式 |
| `build.py` | 組合成 `../index.html` |
| `lib-pinyin-pro.js`, `lib-t2cn.js` | 拼音字典、繁→簡（MIT） |
| `test-engine.js`, `words.txt` | 在 Node 裡測讀音 |

## 規則
- 空格分詞；詞中間的句中標點（，。！？、；：）也當分界，標點跟著前一個詞。
- 每個詞停留秒數依漢字數：1／2／3／4 個字以上，可在畫面上設定。
- 詞後面有標點多停「標點後」秒數；行尾（按 Enter 的換行）多停「換行後」秒數，兩者同時成立只取比較長的。
- 反紅是累積的（念過的保持紅色），播完停在全紅。

```
python3 build.py
```
