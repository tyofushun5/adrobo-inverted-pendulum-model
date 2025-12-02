# adrobo inverted pendulum MJCF

二輪倒立振子の MJCF モデルです。MuJoCo での可視化用に簡単な実行スクリプトを添付しています。

![シミュレーション画面](imgs/inverted_pendulum.png)
![MJCF モデル構造](imgs/inverted_pendulum_mjcf.png)

## 必要環境
- Python 3.10 以降（推奨）
- MuJoCo (Python パッケージ `mujoco`)
- OpenGL 対応の表示環境（MuJoCo ビューワーを使う場合）

## セットアップ
```bash
git clone https://github.com/tyofushun5/adrobo-inverted-pendulum-reinforcement-learning.git
cd adrobo-inverted-pendulum

python -m venv .venv
.\.venv\Scripts\activate          # macOS/Linux: source .venv/bin/activate
pip install mujoco
```

## 実行
付属スクリプトでモデルを表示する手順です。`inverted_pendulum.xml` や STL の相対パスを解決するため、MJCF ディレクトリで実行してください。
```bash
cd inverted_pendulum/MJCF
python inverted_pendulum.py
```

## リポジトリ構成
- `inverted_pendulum/MJCF/inverted_pendulum.xml` : モデル定義（重力・関節・ジオメトリなど）
- `inverted_pendulum/MJCF/inverted_pendulum.py` : モデルを読み込みパッシブビューアで表示する簡易スクリプト
- `inverted_pendulum/MJCF/stl/` : ベース・車輪・ポールの STL メッシュ
- `imgs/` : README 用画像
- `LICENSE`

## 詳細
- `option`: 時間刻み 0.001 s、`integrator="implicitfast"`、重力 `-9.81 m/s^2`
- ボディ: フリーボディのベースに 2 輪（軸ヒンジ）、ポール（可動範囲 -130〜30 度のヒンジ）、先端にボールジョイント質点
- アセット: チェッカーボード床テクスチャ、STL メッシュをスケール 0.001 で読み込み
- ライティング: 2 つのディレクショナルライトでシーンを照明


## ライセンス
- 本リポジトリは MIT License で公開しています。
- 利用・改変・再配布は自由ですが、著作権表示とライセンス全文（`LICENSE`）の同梱が必要です。
- Issue や PR への提案も歓迎します。利用時の注意点・制限事項は `LICENSE` を参照してください。
