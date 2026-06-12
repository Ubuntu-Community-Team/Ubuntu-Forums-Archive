---
title: "[SOLVED] div layout help needed"
date: 2007-09-01
forum: Art &amp; Design
---

### Post by southernman on 2007-09-01
I need to have the "Content" section be colored the whole length of the right column. It has to be a really simple thing to do, but I am overlooking it atm.

Can anyone lend a hand? Please

Screenshot attached also.

Relevant page code:

```

<div id="maincontainer">
			<div id="navbar">
			<a href="#">Link one</a>&nbsp;|&nbsp;
			<a href="#">Link two</a>&nbsp;|&nbsp;
			<a href="#">Link three</a>&nbsp;|&nbsp;
			<a href="#">Link four</a>&nbsp;|&nbsp;
			<a href="#">Link five</a>			
			
			</div>
	<div id="maincontent">
		<h2>Content</h2>
		<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.</p>
	</div>	
	<div id="rtbar">
		<p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.</p>
	</div>
	</div>

```

relevant styles code:

```

/* Main div blocks */
div#navbar { 
	background-color: #1c1c57;
	color: white;
	text-align: right;
	padding: 5px;	
}

div#maincontainer {
	background-color: #f0f0f0;
	width: 840px; /*Width of main container*/
	margin: 0 auto; /*Center container on page*/

}

div#rtbar {
	width: 25%;
	float: left;
	background-color: silver;
}

div#maincontent {
	width: 75%;
	float: left;
	background-color: #f0f0f0;
	color: #000;
}


```

Thanks

---

### Post by southernman on 2007-09-04
Got it to work by moving the footer div to reside in the maincontent div.

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Laminate Installer - Home</title>
<meta http-equiv="content-type" content="text/html; charset=UTF-8" />
<link rel="stylesheet" type="text/css" href="styles.css" />
</head>
<body>
	<div id="header">
		<h1>Header</h1>
	</div>			
		<div id="maincontainer">
			<div id="navbar">
			<a href="#">Link one</a>&nbsp;|&nbsp;
			<a href="#">Link two</a>&nbsp;|&nbsp;
			<a href="#">Link three</a>&nbsp;|&nbsp;
			<a href="#">Link four</a>&nbsp;|&nbsp;
			<a href="#">Link five</a>			
			
			</div>
	<div id="maincontent">
		<h2>Content</h2>
		<p>&nbsp;</p>
	</div>	
	<div id="rtbar">
		<p>&nbsp;</p>
	</div>
	
	<div id="footer">
		<p>Footer</p>
	</div>
	</div>
</body>
</html>

```

Sometimes you just can't see the forest, for the trees!

---

