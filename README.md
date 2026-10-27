# Storm surge simulator (storm_surge) and window app — companion source for the book

Design documents and code for the storm surge simulator built in ***Toward a Million Lines XV — Building a Storm Surge Simulator*** (Japanese title 『LLM で 100 万行のソフトウェア開発 XV — 高潮のシミュレータをつくる』; the book is in Japanese).

`storm_surge` (Python) puts the **pressure** of a typhoon, the **wind**, the **tide** and the **Earth's rotation** into one shallow-water equation. It runs a **global tide** (10 arc-minute grid, tide-generating force, self-attraction and loading, internal-tide drag) and a **regional storm surge** from the north-west Pacific down to Ofunato Bay (nested grids from 3 arc-minutes to about 60 m) for **Typhoon No. 10 of 2016**, and adds **wind waves** (a directional spectrum model), **wave groups** and their force, the **response of a bay**, a **moving pressure band** and a **double Holland** wind and pressure profile. It writes figures and 2-D and 3-D animations. A Windows **window app** (Flutter) sets the parameters of the 8 kinds of calculation, starts them, shows progress and plays the animations. **The window holds no computation of its own**: every button runs a `storm_surge` command and reads the result files it writes. In this project **the design documents are the source of the code**. The results are results of a model, not forecasts.

## Download

**The ready-to-run app and the source are on the [Releases](../../releases) page**, not in this repository. The release has six separate ZIPs:

| File | Contents |
|:---|:---|
| `storm_surge_exe.zip` | The Windows window app, ready built (**Japanese screens**), with the simulator it runs |
| `storm_surge_exe_en.zip` | The same app (**English screens** and English window title by default), with the same simulator |
| `storm_surge.zip` | The Japanese set: design documents (`docs/`, Japanese, L1-L4, 289 files, the source), the code (`src/storm_surge/`, tests, `app/`), and the book (EPUB, manuscript, figures) |
| `storm_surge_en.zip` | The English set: `docs_en/` (all 289 files, L1-L4: **L1-L3 (66 files) translated into English; the 223 L4 files are the Japanese originals as is**), the code, the tests and the source of the window app (built with English as the default screen language) |
| `storm_surge_animations.zip` | The animations of the calculations of the book: 29 MP4 video files (Typhoon No. 10 in eight cases, the global tide, wind waves; the text inside the videos is Japanese) |
| `storm_surge_data.zip` | The data the calculations read (topography, tide and observation data) |

The app needs Python 3.11 and numpy, scipy, numba, matplotlib and pillow on your PC (see the README inside the ZIPs); extract to a short path and put the `data/` folder of `storm_surge_data.zip` in the root of the package. There is **no APK** (the app is a Windows desktop app). The app is **not code-signed**, so Windows may warn you. Computation results are not included. The first run takes a few minutes (numba compiles); the long calculations (31 days of the global tide, the full runs of the typhoon) belong on a GPU or many-core machine; on a notebook PC stop at checking that things run with short settings. The comments in the code are in Japanese, and the progress lines and figure labels written by the simulator are in Japanese in both builds; only the window is switched to English.

You are free to change the design documents and the code and compare the results.

---

## License

- **The author holds the copyright.**
- **The code is under the GNU General Public License v3.0 or later (GPL-3.0-or-later).** The full text is [`LICENSE`](LICENSE). **If you modify it and distribute it, you must publish the source under the same GPL-3.0-or-later terms.**
- **The design documents and the text are under the Creative Commons Attribution-ShareAlike 4.0 International license (CC BY-SA 4.0).** This covers `docs/`, `docs_en/`, the READMEs and the other written text of this repository, and the text of the matching book. See [`LICENSE-DOCS.md`](LICENSE-DOCS.md).
- **If you use them, say so.** State where it came from (the title of the book and the name of this repository) and keep the copyright notice. If you changed it, say that you changed it.
- **In this project the design documents are the source of the code.** When you publish something made from this code, **publish the design documents together with the code.**
- Third-party components (numpy, scipy, numba, matplotlib and pillow installed by `pip`; the Flutter engine inside the EXEs) remain under their own original licenses. The data in `storm_surge_data.zip` stays under the rights of each provider; credit the providers when you publish results.
- Provided "as is", without warranty — as the GPL-3.0 text says.

## 著作権とライセンス

- **著作権は、著者にあります。**
- **コードは、GNU General Public License v3.0 以降（GPL-3.0-or-later）です。**全文は [`LICENSE`](LICENSE) です。**改変して配布するときは、同じ GPL-3.0 以降の条件で、ソースを公開する義務があります。**
- **設計書と文章は、Creative Commons 表示-継承 4.0 国際（CC BY-SA 4.0）です。**このリポジトリの `docs/`・`docs_en/`・README ほかの文章と、対応する本の文章が当たります。内容は [`LICENSE-DOCS.md`](LICENSE-DOCS.md) です。
- **使ったときは、使ったことを書いてください。**どこから使ったか（本の題名と、このリポジトリの名前）と、著作権の表示を、使った先に書いてください。直したときは、直したことも書いてください。
- **このプロジェクトでは、設計書がコードの源です。**コードを使って作ったものを公開するときは、**設計書も、コードと一緒に公開してください。**
- 第三者の部品（`pip` で入る numpy・scipy・numba・matplotlib・pillow、EXE の中の Flutter の engine）は、それぞれの元のライセンスのままです。`storm_surge_data.zip` のデータの権利は、それぞれの提供元に残ります。成果を公開するときは、提供元の表示を付けてください。
- 現状のまま（as is）提供します。保証はありません（GPL-3.0 の全文のとおりです）。
