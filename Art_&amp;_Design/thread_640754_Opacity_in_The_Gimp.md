---
title: "Opacity in The Gimp"
date: 2007-12-14
forum: Art &amp; Design
---

### Post by t.z0n3 on 2007-12-14
How do you change opacity in The Gimp? I can't find the option. 

Also, if anybody would look at my other topic, I still can't update the version to the new one.

---

### Post by digifan on 2007-12-14
try:
[http://www.gimp.org/tutorials/Creating_Icons/](http://www.gimp.org/tutorials/Creating_Icons/)
or
[http://kimihia.org.nz/how/gimpalpha/](http://kimihia.org.nz/how/gimpalpha/)
or
[http://www.linuxnetmag.com/en/issue4/m4gimp1.html](http://www.linuxnetmag.com/en/issue4/m4gimp1.html)
to name a few

---

### Post by smartboyathome on 2007-12-14
You can change opacity by going to layers > transparency > add alpha channel

---

### Post by t.z0n3 on 2007-12-14
I got to 'add alpha channel', but what do you do after that? Nothing happens. No special tool box appears like usual. :(

---

### Post by digifan on 2007-12-14
then you go to menu edit clear Ctrl+K

---

### Post by whiteraven on 2007-12-14
> How do you change opacity in The Gimp? I can't find the option.

Depending on what you are trying to achieve, there at least two ways to change opacity:

1) With the desired layer active, move the Opacity slider at the top of the layers dialog to the level you want - this affects the entire layer.

or

2) Using any of the selection tools, select the area of the layer you want to change. Open the Layer -> Colors -> Curves... dialog and set the Channel option to Alpha. Grab the upper right end of the diagonal line in the graph area and slide it downwards to the amount of alpha transparency you want.

There are other ways, but you will use these two most often. Hope this helps you, and have a look at the online book, [[COLOR="Blue"]Grokking the GIMP[/COLOR]]("http://gimp-savvy.com/BOOK/index.html") is very helpful even though it's a bit dated.

---

### Post by jmadero on 2008-11-06
I know that this is a really old thread but I had to say THANK YOU! I've been looking for stuff on opacity and transparency forever and I keep finding how to make the background transparent but I wanted to make the whole image transparent (like a watermark) and it was as simple as showing the layers and sliding the opacity bar down...THANKS!

---

