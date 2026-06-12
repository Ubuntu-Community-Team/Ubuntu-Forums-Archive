---
title: "[web design] stack two floating elements"
date: 2011-08-17
forum: Art &amp; Design
---

### Post by maclenin on 2011-08-17
Hello!

Essentially, I have two horizontal lists that I'd like to stack on top of one another - using float - to (easily) maintain a 10px margin between each item:

list A
```
#item1,
#item2,
#item3,
#item4,
#item5 {position:relative; top:10px; float:right; margin-right:10px;} 
```

list B
```
#item6,
#item7,
#item8,
#item9,
#item10 {position:relative; top:30px; float:right; margin-right:10px;}
```

The result I am shooting for:

 ```
 item1  item2  item3  item4  item5

item6  item7  item8  item9  item10
```

Floating list A or list B (in the manner indicated via CSS) without the other list (A or B) - works fine - but I can't seem to float the two (A and B), together.

Thanks for any insight!

---

### Post by maclenin on 2011-08-18
I think I solved the riddle:

CSS
```
/*list_B_container*/
#list_B {position:absolute; left:10px; top:30px; width:100px; height:20px;}
```

HTML
```
<div id="list_B">
<div id="item6">item6</div>
<dib id="item7">item7</div>
<div id="item8">item8</div>
<div id="item9">item9</div>
<div id="item10">item10</div> <!--list B items floating inside their container just underneath list A-->
<div> <!--list_B_container closing tag-->
```

Any thoughts or critique welcome!

Hope this helps someone else....

---

### Post by Dragonbite on 2011-08-18
Wow.. I thought this would be easier than it is.  

I threw together some CSS and it worked... in IE.  Then I got it working in Chrome and Firefox, but IE adds another row. Argh!

This is the code that I got to working:

The HTML portion ```
<div id="listA">
	<div> item01 </div>
	<div> item02 </div>
	<div> item03 </div>
	<div> item04 </div>
	<div> item05 </div>
</div>
<div style="float:none; ">&nbsp;</div>
<div>
	<div id="listB">
	<div> item6 </div> 
	<div> item7 </div>
	<div> item8 </div>
	<div> item9 </div>
	<div> item10 </div>
</div>
``` The middle div, with "float:none;" will stop the float action until the next <div> element, under listB, re-enacts the float.  This allows the two <div> "rows" to go on separate lines.

Unfortunately, in IE that middle <div> shows up as a blank row while Firefox and Chrome does not.

The CSS in the header portion is this ```
#listA { display:block; width:100%; color:red;	}
#listA div
	{
	float: left;
	padding-left: 10px;
	padding-right: 10px;
	width:80px;
	}
#listB { display: inline; width:800px; color:Blue; }
#listB div
	{
	float: left;
	padding-left: 10px;
	padding-right: 10px;
	width:80px;
	}
```  I cannot say I am 100% sure if this is right, or what but like I said it displays as you are looking for (with a couple of changes to line them up, and color them to show that the style actually is being used).

Hopefully somebody can shed some light on this.

---

### Post by Dragonbite on 2011-08-18
Wow.. why didn't I think of this earlier. This is actually easier than I thought by using <span> instead.

Unfortunately the Width CSS is only effective in IE (and Chrome?) and lines up the items in a more grid-like setup. Firefox  does not.

I purposely staggered the text portion so they are a different width so you can see the difference if you look at it in Chrome/IE and Firefox.

So here is the code for a complete page that displays it the way you are looking at (I think)
```
<html>
<head>
<title>Display grid 2x5</title>
	<style type="text/css">
		div span 
			{
			padding-left: 10px;
			width:100px;
			color:Red;
			}
	</style>
</head>
<body>
	<span>This span should <b>NOT</b> be in Red.<br />That is because the span style defined (above) will only do a 
	<span lang="en-us">&lt;span&gt;</span> that is in a <span lang="en-us">&lt;div&gt;</span> tag.<br />
	<span lang="en-us">The CSS can be edited to only edit the &lt;span&gt; in a named 
	&lt;div&gt; by using #divID span { } instead.</span><br />
	</span>
	&nbsp;

	<div>
		<span> item1 </span>
		<span> item 2 </span>
		<span> item3 </span>
		<span> item 4 </span>
		<span> item5 </span>
	</div>
	<div>
		<span> item 6 </span> 
		<span> item7 </span>
		<span> item 8 </span>
		<span> item9 </span>
		<span> item 10 </span>
	</div>

</body>
</html>

```

The key is that while a <div> usually stretches across the page, a <span> stays in line.  So you can use <span> to edit a word in a sentence with no problems, but if you use <div> you have to use float: and then the portion right afterwards also becomes a mess.

---

