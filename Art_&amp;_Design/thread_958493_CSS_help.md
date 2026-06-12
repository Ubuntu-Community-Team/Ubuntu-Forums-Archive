---
title: "CSS help"
date: 2008-10-25
forum: Art &amp; Design
---

### Post by susanpenter on 2008-10-25
I'm hoping there is some one out there who knows their way around CSS as the W3 Schools forum is short of band with again.

All I am trying to do is have a top box two side by side boxes below it and a footer box at the bottom.  If I put the right hand box in the absolute position the footer cuts into it and I don't want to define a height as not all pages are the same.  Thanks in advance

Here is the code:
#body {
background-color:#CCCCCC;
}

#search {
text-align:center;
background-color:#B03060;
color:#FFFFFF;
position:absolute; left:5%; top:10px;
padding:5px;
height:100px;
width:90%;
}

#page {
background-color:#FFFFFF;
width: 90%; height: auto;
position: absolute; left:5%; top:100px;
padding:5px;
border:5px;
}

#lefthalf {
width:50%;
position:static;
text-align:center;
height:auto;
padding:5px;
}

#righthalf {
width:50%;
position:relative;
top:0px;
left:50%;
text-align:center;
height: auto;
padding:5px;
}


#footer {
height:auto;
background-color:#ffffff;
padding:5px;
text-align:center;
}

---

### Post by Merk42 on 2008-10-25
Without seeing the part in the <body> it's difficult to troubleshoot.

Instead are these of any help?
[http://www.dynamicdrive.com/style/layouts/category/C9/](http://www.dynamicdrive.com/style/layouts/category/C9/)
[http://www.456bereastreet.com/lab/developing_with_web_standards/csslayout/2-col/](http://www.456bereastreet.com/lab/developing_with_web_standards/csslayout/2-col/)

---

### Post by susanpenter on 2008-10-25
> **Merk42 said:**
> Without seeing the part in the <body> it's difficult to troubleshoot.

Instead are these of any help?
[http://www.dynamicdrive.com/style/layouts/category/C9/](http://www.dynamicdrive.com/style/layouts/category/C9/)
[http://www.456bereastreet.com/lab/developing_with_web_standards/csslayout/2-col/](http://www.456bereastreet.com/lab/developing_with_web_standards/csslayout/2-col/)

Thanks for that, I have decided that for this site I will leave it with built in styles as each page is different.  I'll keep separate style sheets for my new sites.

Cheers anyway,
Susan

---

### Post by Free Hugs on 2008-10-27
I'm not sure if this exactly answers your question, but if you haven't already, download the firebug extension for firefox.

This way, you can edit the CSS "live" and see how it manipulates your document.

I wouldn't abandon coming up with a clever design just because it's easier to code each page individually. (Unless it's a static sub-10-page site to begin with). 

There are plenty of ways around this problem, but you might have to compromise. For instance: creating a <div> container that has a fixed width and then floating two divs (specify their width also) inside of it should give you the result you want...something like this:

```
<div id="header" style="width:100% height:100px; margin:0px;">Top Bar Content Here</div>
<div id="wrapper" align="center" style="width:100%">
<div id="content_wrapper" align="left" style="width:900px;">
<div id="left_content" style="float:left; width:450px;"></div>
<div id="right_content" style"float:left; width:450px;"></div>
</div></div>
<div id="footer" align="center" style="width:100%">Footer Here</div>
```

BTW...inline CSS should be avoided. Use classes to your advantage. You can make incremental changes by specifying a class and an ID, and it makes organization very easy, and it makes tracking mistakes VERY easy...because you always know exactly where the CSS is - in your style_name_here.css file.
Start a good habit now and go external with your CSS.

---

### Post by susanpenter on 2008-10-27
Thanks free hugs, I really would like to use external CSS and with new sites I hope to do that but one of my problems is that so many different browsers render sites differently.  The site I have been talking about is my main web design site  - I am good enough at web design to set up sites for small businesses etc I just need to get up to speed with other codes.  I see other pro am level users like myself are still styling with table to avoid the problems of older browsers not being able to read sites totally styles by CSS.

Thanks

---

### Post by xoger on 2008-10-28
html solution

[HTML]
<html>
<body>
<table width = "100%" hight = "100%">
<tr>
<td cospan = "2">
//banner
</td>
</tr>

<tr>
<td>
// left-handbox
</td>
<td>
// right-hand box
</td>
</tr>

<tr>
<td cospan = "2">
// footer
</td>
</tr>
</table>
</body>
</html>
[/HTML]

i recommend this because most websites use HTML for the layout

---

### Post by Peter76 on 2008-10-28
@xoger: using tables for layout is not the way to go anymore these days. The standard compliant way of doing things is, is to markup your content in HTML and do the layout in CSS

---

### Post by xoger on 2008-10-28
that's complicated for the sake of it, give me one advantage of doing that

---

### Post by Merk42 on 2008-10-28
> **xoger said:**
> i recommend this because most websites use HTML for the layout

Using div tags is still html...

> **xoger said:**
> that's complicated for the sake of it, give me one advantage of doing that

[Well this is more than one...](http://www.hotdesign.com/seybold/everything.html)

---

### Post by xoger on 2008-10-29
i know a lot of people are saying that <div> tags should be used but i personally prefer tables because they are straight forward. if anyone wants to do it a different way, thats fine by me.:biggrin:

---

