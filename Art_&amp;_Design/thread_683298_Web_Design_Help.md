---
title: "Web Design Help"
date: 2008-01-30
forum: Art &amp; Design
---

### Post by spyder0101 on 2008-01-30
I am making a web site and experimenting with using css for positioning.  Right now I am having some troubles getting my boxes in the right position.  In Firefox, everything looks perfect.  In IE, the right box is down below the left box.  Can anyone tell me why?

Thanks, 
Spyder

```

ul{
	list-style-type:none;
}

#Container {
	left: 0px;
	top: 0px;
	width: 820px;
	position: relative;
	margin-right: auto;
	margin-left: auto;
}

#header {
	float: left;
	left: 0px;
	top: 0px;
	width: 820px;
	height: 364px;
	background-image: url('images/head1.png');
}

#header ul.navi{
	width: 750px;
	display: block;
	position: absolute;
	top: 330px;
	left: 80px;
	padding: 0;
	margin: 0;
	background: none;
}

#header ul.navi li{
	border-width: 1px;
	height: 22px;
	padding: 0 18px 0 5px;
	margin: 0;
	display: block;
	float: left;
}

#header ul.navi li.li1{
	background:none;
	height:22px;
	padding:0 14px 0 5px;
	margin:0;
	display:block;
	float:left; 
}

#header ul.navi li a{
	font: 12pt Arial, Helvetica, sans-serif;
	color: #000000;
	text-decoration: none;
	text-indent: 0px;
	padding: 0 0 0 33px;
	font-weight: bold;
	margin: 0;
	width: inherit;
	letter-spacing: -1px;
}

#header ul.navi li a:hover{
	color: #000000;
	text-decoration: none;
}

#left {
	float: left;
	left: 0px;
	top: 384px;
	width: 266px;
}

#left h2{
	font: 30px/24px "Calisto MT";
	color: #000000;
	font-weight: normal;
	display: block;
	letter-spacing: -1px;
	word-spacing: 0em;
	text-indent: 0px;
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 10px;
	padding-top: 0px;
	padding-left: 55px;
}

#left p{
	background: no-repeat;
	color: #000000;
	padding: 0 0 0 55px;
	width: 190px;
	display: block;
	font: 13px/20px "Trebuchet MS";
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 0;
	letter-spacing: 0px;
}

#left p span{
	color: #000000;
	font-weight: bold;
	font-size: 16px;
	letter-spacing: -1px;
}

#left p span.bg{
	color: #000000;
}

#left p a{
	font: 13px/12px "trebuchet MS";
	font-weight: normal;
	color: #000000;
	text-decoration: underline;
	padding-top: 0;
	padding-right: 0;
	padding-bottom: 0;
}

#left p a:hover{
	background: no-repeat;
	color: #000000;
	font-weight: normal;
}

#right {
	float: left;
	left: 266px;
	top: 384px;
	width: 554px;
}

#right h2{
	font: 30px/24px "Calisto MT";
	color: #000000;
	font-weight: normal;
	display: block;
	letter-spacing: -1px;
	word-spacing: 0em;
	text-indent: 0px;
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 10px;
	padding-top: 0px;
	padding-left: 20px;
}

#right p{
	background: no-repeat;
	color: #000000;
	padding: 0 0 0 20px;
	width: 490px;
	display: block;
	font: 13px/20px "Trebuchet MS";
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 0;
	letter-spacing: 0px;
}

#right p span{
	color: #000000;
	font-weight: bold;
	font-size: 16px;
	letter-spacing: -1px;
}

#right p span.bg{
	color: #000000;
}

#right p a{
	font: 13px/12px "trebuchet MS";
	font-weight: normal;
	color: #000000;
	text-decoration: underline;
	padding-top: 0;
	padding-right: 0;
	padding-bottom: 0;
}

#right p a:hover{
	background: no-repeat;
	color: #000000;
	font-weight: normal;
}

```

---

