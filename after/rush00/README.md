Author:
    yusyamas (42Tokyo C Piscine 2022/10)

Subject:
    subjectフォルダのpdfがベース
    ボーナス問題としてコマンドライン引数からx,yの入力を受け取る
    ただし、あり得ないx,yについてはError出力をしなければならない

Run:
    makeで自前のサンプルでの検証結果をoutputファイル内のsample.txtに書き出す

受験時点でのrush00の解答の改善点の修正と、
makefile、ヘッダファイル、シェルスクリプトの練習をしたもの
makefileはrelinkしないはず

・改善点
    ・rush0X.cで、x座標、y座標を分離せずに処理していたのを、座標軸でそれぞれ分離して処理させるようにした
    ・main.cでargcが3でなかった場合に、エラーフラグを立てず、x,yを初期化していなかったため、エラー処理がなされず最適化によって適当に決められたx,yがrush0X.cで走ってしまう事故が起きていたため、x,yをエラーが起きる-1で初期化し、argc=3の場合のみatoiの処理を行い、その後に全てのパターンでエラー判定の処理を行わせた
    ・上の変更を行うついでに、atoiでx,yがエラー文字列だった場合にintへの変換結果を-1として返させるようにした

・注意点
    ・main.cでエラーケースを弾いても、mainのrush(x,y)のx,yに直接書き込んでrush0X.c内での未定義動作とエラー出力できるかどうかを確認されるのでrush0X.cでもエラー判定をしなければならない
    ・その過程でエラー判定関数がmain.cとrush0X.cで同じなので、main.c内のエラー判定関数を呼び出させるように変更した