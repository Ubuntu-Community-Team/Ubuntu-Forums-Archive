---
title: "[SOLVED] Newbie needs web site help."
date: 2008-07-05
forum: Art &amp; Design
---

### Post by majikhotline on 2008-07-05
Hello ubuntu country,
I wanted to thank everyone for their dedication for this forum.
Im trying to figure out html code. This is what I have to make a picture (headshot1.jpq) show up on my index.html site.

```
<td bordercolor="1" width="265"><img src="images/headshot1.jpg" align="right" border="0" height="324" width="256"></td></tr>
```

My index.html and images folder are in the same dir, which is in var/www/ and I change the privilige to 777 (var/www/*)

What everyones suggestions on how to get the picture to show up.

Thanks:KS

---

### Post by era86 on 2008-07-05
Do you just get red x's?  This could be several problems.

---

### Post by cariboo on 2008-07-05
Try using the full path to your image:

```
/var/www/images/headshot1.jpg
```

THe permissions should be 755 and the owner and group should be root.root or www-data.www-data

Jim

---

### Post by majikhotline on 2008-07-05
My files are in /var/www, I tried
```
<img src="/var/www/images/headshot1.jpg" align="right" border="0" height="324" width="256">
```
And I still have no picture, what else could it be?

So frustrating!!!!!!!!:(

---

### Post by majikhotline on 2008-07-05
yes i get the red X's for pictures when I use a windows internet explorer

---

### Post by AJB2K3 on 2008-07-06
I think you need to read through 
[http://www.w3schools.com]("http://www.w3schools.com")
The buy a book on Xhtml before making a web site.

---

### Post by the_hardy_kid on 2008-07-07
Are you sure you have the right filename?

Is it a gif?

Post the location of the image
(e.g /home/joebloggs/Pictures/picture.jpg)

And your entire HTML code.

I'll see what i can do. :)

---

### Post by scragar on 2008-07-07
if your using a file path starting at / then the path should start:
```
<img src='file:///**....**'>
```
if the path is on the local host but in a directory above your host refer to it using a path from /var/www like so:
```
<img src='/**....**'>
```
and if it's from the current directory then like so:
```
<img src='**....**'>
```

If the image doesn't load try running:
```
javascript:for(i in document.images){if(i.src){window.open(i.src)}}
```
from the URL bar, see what your pop-ups URLs look like.

---

