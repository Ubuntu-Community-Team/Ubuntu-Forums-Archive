---
title: "Put up a website"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-20
i have a really beginner and maybe sily question, can anyone give me a link or a howto on "how to" put up a website, from a to z, as in from creating the website on ur pc using a certain software to getting a domain and server and all that and how it really works.
im sorry if this is a very low pitch!!
thanks anyways.

---

### Post by Cardmaster91 on 2006-11-20
i think you are in the wrong forum, this really has nothing to do with linux. but here is a good website, this is how i learned html and java, and css, all that. 
[http://www.w3schools.com/]("http://www.w3schools.com/")


i copied this from there side panel

HTML Tutorials
Learn HTML
Learn XHTML
Learn CSS
Learn TCP/IP

XML Tutorials
Learn XML
Learn XSL
Learn XSLT
Learn XSL-FO
Learn XPath
Learn XQuery
Learn XLink
Learn XPointer
Learn DTD
Learn Schema
Learn XML DOM
Learn XForms
Learn SOAP
Learn WSDL
Learn RDF
Learn RSS
Learn WAP
Learn Web Services

Browser Scripting
Learn JavaScript
Learn HTML DOM
Learn DHTML
Learn VBScript
Learn AJAX
Learn E4X
Learn WMLScript

Server Scripting
Learn SQL
Learn ASP
Learn ADO
Learn PHP

.NET (dotnet)
.NET Microsoft
.NET ASP
.NET Mobile

Multimedia
Learn Media
Learn SMIL
Learn SVG
Learn Flash

Web Building
Web Building
Web W3C
Web Browsers
Web Quality
Web Semantic
Web Careers
Web Hosting
Web Certification




and for a hosting service, i would just google it. there are plenty of free ones, but they are limited to one sort of thing, and it kind of depends in your needs. if you are willing to pay, i would tyr yahoo (geoocities.com or something like that). idk of any free editior, (ubuntu may have one) but frontpage is pretty good, u can get a 30-day trial of dreamweaver from macromedia [click here for free trial]("https://www.adobe.com/cfusion/tdrc/index.cfm?product=dreamweaver&loc=en%5Fus")

---

### Post by aysiu on 2006-11-20
I would highly suggest you read [Liz Castro's *Visual Quickstart Guide to HTML, XHTML, and CSS*](http://www.amazon.com/XHTML-Sixth-Visual-Quickstart-Guide/dp/0321430840/sr=8-1/qid=1164002697/ref=pd_bbs_sr_1/002-5619415-5595256?ie=UTF8&s=books). That's what got me and my wife started on basic webpage design.

Just some general principles, though:

Webpages are essentially text files. To create an extremely basic webpage, use a text editor like Gedit, put in this code: ```
<html>
<head>
<title>My first webpage</title>
</head>
<body>
Hey, this is my first webpage, everybody!
</body>
</html>
``` Then save it as index.html on your desktop. Right-click that file and choose to **open with** Firefox and you'll see it as a webpage.

To get it actually published so other people can see it, you need to upload that file to a webserver. Some people have a private web server hosted somewhere. Others use "free" services ("free" = full of advertisements) to host webpages. Still others create their own server at home (maybe that server is Ubuntu!).

Once you upload it, anyone can just visit your address and see your page.

Now, in terms of learning HTML, I would highly recommend that book. You can check it out of the library if you want, read it in a bookstore, or actually buy it.

---

### Post by Mazen on 2006-11-20
ya i guess i was in the wrong forum but i just like to post here! lol i get good help, well just like the one u gave me right now!!:)
thanks

---

### Post by Cardmaster91 on 2006-11-20
no problem, teaching yourself code is pretty didficult, but w3schools is straight forward. i learned html in like 3 days. once you understand the structure, it will become incredibly easy

---

### Post by aysiu on 2006-11-20
> **Cardmaster91 said:**
> no problem, teaching yourself code is pretty didficult, but w3schools is straight forward. i learned html in like 3 days. once you understand the structure, it will become incredibly easy
It's actually not that tough if you *don't* teach yourself, which is why I recommended Liz Castro's book.

Some basic tags to give you a sense of what's up ahead (and I'd learn HTML first before even thinking about CSS):

<b>bolds whatever is in between these two tags</b>
<u>underlines whatever is between these two tags</u>
<i>italicizes text</i>
<font color="#000000">makes the text black</font>
<font color="#ffffff">makes the text white</font>
<ul>
<li>item in a bullet-point list
<li>next item in the list
<li>still another item in the list
</ul>
<ol>
<li>item in an ordered list
<li>next item in the list
<li>still another item in the list
</ol>

Basically, surrounding text with tags changes its appearance. Try it with that test *index.html* file I asked you to create before. Change it to this and see how the changes are reflected when you open it in Firefox: ```
<html>
<head>
<title>My first webpage</title>
</head>
<body>
<font color="#e0e0e0">Hey</font>, <b>this</b> <i>is</i> <u>my</u> <font color="#00a5c6">first webpage,</font> <font face="arial">everybody!</font>
</body>
</html>
```

---

### Post by Hmarroqu on 2006-11-20
to make this a little related to this forum, why not try Nvu? great program for developing a webpage.  I used it to set up my businesses page and is pretty what u see is wat u get.

as for free hosting, try angelfire.com....its ok and pretty easy with its tutorials

---

### Post by Cardmaster91 on 2006-11-20
i think angelfire is like the same thing as geocities, or is owned by same people. they have templates that you can edit thru there interface, wil make a pretty simple wbsite.

---

### Post by 3rdalbum on 2006-11-20
I agree, Liz Castro's book is even handy to keep around as a reference manual.

Dreamweaver 8 runs on Linux through WINE; that'll make website creation easy for you.

---

### Post by thinklife on 2006-11-20
There are lots of free host that does not place ads on your webpages.
And they much better than geocities,angelfire etc..
And they have php support,frontpage extension and MySql Databases etc.
I used zeeblo hosting...
xmgfree is another good one.

---

