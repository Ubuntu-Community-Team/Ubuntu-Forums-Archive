---
title: "Script Syntax"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Hasen_A on 2008-03-31
Hello,

I want to save myself the trouble of reediting my welcome website with picasa2 everytime I have made new sub picture galleries. I am therefore creating a little script which is supposed to read the existant subfolders under **~/Sites/** and edit the already available file **~/Sites/index.html**. I am going to refer to the variable **FOLDERNAME** and **FIRSTPICTURE,** for explanation, since I am not sure how variables are declared and what their proper syntax is. A picture gallery created by Picasa2 contains a folder containing the following:
```

~/Sites/FOLDERNAME_1$ ls
images      logo.gif   target0.html  target2.html  target4.html
index.html  style.css  target1.html  target3.html  thumbnails FOLDERNAME_1 ...
```
My goal is to for example read out FOLDERNAME_1 using a string array named FOLDERNAME using the command:

```
ls ~/Sites -p | grep / |grep thumbnail -v | grep images -v
```

this lists all the available folders to standard output, but how do I assign them to a string array named FOLDERNAME?

Corresponding to each folder found by ls, I then want to insert the following line into the already existant index.html at line X 
```
<a href="FOLDERNAME/index.html"><img ali ...> in ~/Sites/index.html
```
where 'FOLDERNAME' denotes the real folder name according to string array value given by the ls and grep commands above.

I am wishing to the exactly the same for the variable 'FIRSTPICTURE' in the same line, but the implemtation should be the same.

my index.html reads as follows

[PHP]<html>

<head>

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<title>Picture Gallery</title>

<link rel="stylesheet" href="style.css" type="text/css">

</head>

<body bgcolor="#FFFFFF" text="#000000">

<span class="textbg">Andy's Picture Gallery</span><br>

<span class="textsm"></span>

<p class="desc"><p><span class="textreg">Toulouse 2007-2008 : Click a picture gallery.</span><br>

<hr size="1">

<a href="FOLDERNAME/index.html"><img align="center" src="FOLDERNAME/thumbnails/FIRSTPICTURE" title="FIRSTPICTURE" border="0"></a>

<map name="Map">

  <area shape="rect" coords="95,1,129,44" href="frameset.htm">

</map>

</body>

</html>[/PHP]

---

### Post by cmnorton on 2008-03-31
FOLDERNAME=`ls ~/Sites -p | grep / |grep thumbnail -v | grep images -v`

---

### Post by Hasen_A on 2008-04-01
Thank you for your reply. How is the syntax for the variable 'FOLDERNAME' implemented into the HTML code?

```
<a href="FOLDERNAME/index.html"><img align="center" src="FOLDERNAME/thumbnails/FIRSTPICTURE" title="FIRSTPICTURE" border="0"></a>
```

Could you maybe direct me to a good website explainig bash scripting? The one's I've found so far didn't help me much.

---

