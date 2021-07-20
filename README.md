<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8">
<title>三択クイズ</title>
</head>
<body>
<h1>三択クイズ</h1>
<hr>
<h2>問題</h2>
<div id="text_q"></div>
<h2>選択</h2>
<div id="text_s"></div>
<h2>解答</h2>
<div id="text_a"></div>

<script type="text/javascript">
//問題と解答
qa = new Array();
qa[0] = ["男子100mの世界記録はどれ？","9.69","9.58","9.49",2];
qa[1] = ["マイルリレーとはどの略？","4×200m","4×400m","4×100m",2];
qa[2] = ["女子100mの世界記録はどれ？","10.59","10.63","10.49",3];
qa[3] = ["男子100m日本記録は？","9.95","9.97","9.85",1];
qa[4] = ["2021年現在の100m日本記録保持者は誰？","サニブラウンAハキーム","山縣亮太","桐生祥秀",2];
qa[5] = ["2021年現在男子三段跳の日本記録は何年破られてないか？","21年","15年","34年",3];
qa[6] = ["室伏広治伝説のうち間違っているものは？","手投げで131km 野球","練習で立ち幅跳び世界記録","アジア選手権でなんとなくでた槍投げで2位",3];
qa[7] = ["女子1500mの日本記録保持者は誰？","田中希実","卜部蘭","北村夢",1];
qa[8] = ["女子100m記録は誰？","フレーザープライス","土井杏奈","福島千里",3];
qa[9] = ["室伏広治は日本選手権何連覇しましたか？","7連覇","11連覇","18連覇",2];

//初期設定
count = 0; //問題番号
q_sel = 3; //選択肢の数

//最初の問題
quiz();

//問題表示
function quiz() {
	var s, n;
	//問題
	document.getElementById("text_q").innerHTML = (count + 1) + "問目：" + qa[count][0];
	//選択肢
	s = "";
	for (n=1;n<=q_sel;n++) {
		s += "【<a href='javascript:anser(" + n + ")'>" + n + "：" + qa[count][n] + "</a>】";
	}
	document.getElementById("text_s").innerHTML = s;
}

//解答表示
function anser(num) {
	var s;
	s = (count + 1) + "問目：";
	//答え合わせ
	if (num == qa[count][q_sel + 1]) {
		//正解
		s += "○" + qa[count][num];
		ansers[count] = "○";
	} else {
		s += "×" + qa[count][num];
		ansers[count] = "×";
	}
	document.getElementById("text_a").innerHTML = s;
	
	//次の問題を表示
	count++;
	if (count < qa.length) {
		quiz();
	} else {
		//終了
    s = "<table border='2'><caption>成績発表</caption>";
		//1行目
		s += "<tr><th>問題</th>";
		for (n=0;n<qa.length;n++) {
			s += "<th>" + (n+1) + "</th>";
		}
		s += "</tr>";
		//2行目
		s += "<tr><th>成績</th>";
		for (n=0;n<qa.length;n++) {
			s += "<td>" + ansers[n] + "</td>";
		}
		s += "</tr>";
		s += "</table>";
		document.getElementById("text_q").innerHTML =s;
    //次の選択肢
		s = "【<a href='javascript:history.back()'>前のページに戻る</a>】";
		s += "【<a href='javascript:setReady()'>同じ問題を最初から</a>】";
		s += "【<a href=''>次の問題に進む</a>】";
		document.getElementById("text_s").innerHTML = s;
	}
}
//初期設定
q_sel = 3; //選択肢の数

setReady();

//初期設定
function setReady() {
	count = 0; //問題番号
	ansers = new Array(); //解答記録
	
	//最初の問題
	quiz();
}




</script>
</body>
</html>
