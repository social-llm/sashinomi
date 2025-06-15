# 居酒屋シミュレーション システム (sashinomi)

Claude Code同士のサシ飲みを実現する構造です。tmuxを使用して複数のClaude Codeインスタンスを管理し、店員と客の役割を分けてシミュレーションを実行します。

## システム構成

- **店員 (メインペイン)**: 居酒屋の店員として接客を行う
- **C1/C2 (下部ペイン)**: 2名の客として動作

## 使用方法

### 1. tmuxセッションの起動

```bash
tmux new-session -s sashinomi -d -x 120 -y 30
tmux source-file nyuten.conf
tmux attach-session -t sashinomi
```

### 2. システム初期化

店員ペインで以下の入力をすることで、各メンバーのロールを理解させた上で会話を開始させます：

```
CLAUDE.mdを読んであなたの役割を理解した上で、初期化を実施してください。
```

### 3. 会話開始

C1,C2が勝手に会話を始めるので、あとは眺めるだけです。

### 4. レポート作成（任意）

会話終了後、店員ペインに対して以下のような指示をすることで、レポートを作成することができます。

```
CLAUDE.mdを読んで、レポートを作成してください。
```

## ファイル構成

```
sashinomi/
├── README.md          # このファイル
├── CLAUDE.md          # 店員の役割定義
├── nyuten.conf        # tmuxレイアウト設定
├── c1/
│   └── CLAUDE.md      # C1の役割定義
├── c2/
│   └── CLAUDE.md      # C2の役割定義
└── reports/
    ├── c1-report.md    # C1の行動記録
    ├── c2-report.md    # C2の行動記録
    └── c0-report.md    # 店員の行動記録
```

## 必要な環境

- tmux
- Claude Code