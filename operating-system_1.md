<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
 MathJax.Hub.Config({
 tex2jax: {
 inlineMath: [['$', '$'] ],
 displayMath: [ ['$$','$$'], ["\cr[","\cr]"] ]
 }
 });
</script>

## Operating System

### (CC-BY 4.0) 2024 Taniii.com

### 2024-08-03

---

### 01-2.pdf

#### (1) OS の資源管理はなぜ必要となるのか説明せよ

OS の資源管理は、以下の理由から必要となります：

- **効率的な資源利用**：複数のプログラムやユーザが同時にコンピュータ資源（CPU、メモリ、ディスクなど）を共有するため、資源を効率的に配分することが求められます。
- **競合の防止**：複数のプログラムが同時に同じ資源を要求する場合に競合が発生しないようにする必要があります。OS はこの競合を調整し、適切に資源を割り当てます。
- **安定性と信頼性の向上**：適切な資源管理により、システムの安定性と信頼性が向上し、予期しないクラッシュやデータの損失を防ぐことができます。

#### (2) OS による資源管理を行わない場合どの様な問題が生じると考えられるか

OS による資源管理を行わない場合、以下のような問題が生じます：

- **資源の浪費**：一部のプログラムが必要以上に資源を占有することで、他のプログラムが必要な資源を利用できず、全体として資源が有効に活用されない。
- **競合の発生**：複数のプログラムが同時に同じ資源を要求する場合に競合が発生し、データの破損やプログラムの異常終了を引き起こす可能性がある。
- **システムの不安定化**：資源が適切に管理されないと、システム全体の動作が不安定になり、予期しないクラッシュやハングアップが頻発する。

#### (3) OS が管理する資源を利用する形態についてまとめよ

- **時間貸し**：

  - 資源を一定の時間単位で割り当てる方法。例えば、CPU スケジューリングでは、各プロセスに対して一定の時間スライスを割り当てる。
  - プロセッサ、キーボード、マウス、ネットワークなどの時間分割が適用される資源。

- **空間貸し**：
  - 資源を空間的に分割して割り当てる方法。メモリ管理などで用いられる。
  - ハードディスク、メモリなどの空間分割が適用される資源。

#### (4) OS が提供するインターフェースに関して

- **ユーザインターフェースとしてどのようなものが使用可能か**：

  - **グラフィカルユーザインターフェース (GUI)**：Windows や MacOS のような視覚的な操作が可能なインターフェース。
  - **キャラクタベースユーザインターフェース (CUI)**：UNIX システムや MS-DOS のようなコマンドラインで操作するインターフェース。

- **プログラミングインターフェースの使用方法を説明せよ**：

  - **API (Application Programming Interface)**：OS が提供する機能をプログラムから呼び出すためのインターフェース。C 言語の`printf()`や`scanf()`などの標準ライブラリ関数もこれに含まれる。
  - **システムコール**：OS のカーネルが提供する機能を利用するための関数。例として、UNIX 系 OS の`open()`や`read()`などがある。

- **ライブラリ関数とシステムコール関数の違いを述べよ**：

  - **ライブラリ関数**：プログラムから利用するための高レベルのインターフェース。OS に依存しない標準的な関数（例：`printf()`）。
  - **システムコール関数**：OS のカーネル機能を直接利用するための関数。OS に依存し、ハードウェアとの直接的なやり取りを行う（例：UNIX の`fork()`）。

- **2 つのシステムが互換性を有するとはどのような意味か述べよ**：

  - 互換性とは、2 つのシステムが同じインターフェースを提供し、それを利用するプログラムがどちらのシステムでも同様に動作することを指す。

- **互いに互換性のないシステムで、同じプログラムを動作させるために必要な処理を説明せよ**：
  - 互換性のないシステム間でプログラムを動作させるためには、プログラムの移植が必要となる。具体的には、API の違いを吸収するためにソースコードの修正や再コンパイルが必要となる。

#### コマンド言語を利用したプログラムの入出力の変更に関して

1. **prog1 の入力を a.txt に切り替え、その出力を prog2 への入力とする**：
   '''sh
   prog1 < a.txt | prog2
   '''

2. **prog1 の入力を a.txt に切り替え、その出力を prog2 への入力とし、prog2 の出力を prog3 への入力とする。prog3 の出力を b.txt へ切り替える**：
   '''sh
   prog1 < a.txt | prog2 | prog3 > b.txt
   '''

#### \*フィルタコマンドにどのようなものがあるか調べよ

フィルタコマンドは、入力を受け取り処理して出力を行うコマンドです。代表的なものとして、`grep`、`sort`、`awk`、`sed`、`cut`などがあります。

#### \*リダイレクトを使用する利点にどのようなものがあるか検討せよ

- 入出力の柔軟な管理が可能。
- プログラムの標準出力をファイルに保存できるため、結果を後で確認できる。
- 標準入力をファイルから読み取ることで、同じ入力データを何度も使用できる。

#### \*パイプにより複数のプログラムを組み合わせて処理することの利点を検討せよ

- 各プログラムの出力を次のプログラムの入力として直接渡すことで、中間ファイルを作成する手間を省ける。
- 一連の処理を一つのコマンドラインで実行できるため、操作が簡潔で効率的。
- 単機能のプログラムを組み合わせることで、複雑な処理を実現できる。

<footer>
<p style='font-size: 0.7rem;'>(CC-BY 4.0) 2024 Taniii.com</p>
</footer>
