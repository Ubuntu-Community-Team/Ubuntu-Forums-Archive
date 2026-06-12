---
title: "GIMP...&quot;save for web&quot;????"
date: 2007-03-08
forum: Art &amp; Design
---

### Post by Support the 2nd on 2007-03-08
Does GIMP have something like Photoshops "save for web" feature where I can control the file size/quality of .jpg, .gif, etc.?

---

### Post by smartalecks on 2007-03-08
there is no direct equivalent that I know of.

sorry :/

---

### Post by jem7v on 2007-03-09
Well Actually...
Using Save As, choose your file format as .jpg then click Save and it'll bring up a dialogue box that lets you set the compression/quality level. There will be a little checkbox you can use to turn on a preview in the image window itself.
I haven't experimented much with .gifs in the Gimp, though, so I can't help you there.

---

### Post by Support the 2nd on 2007-03-09
> **jem7v said:**
> Well Actually...
Using Save As, choose your file format as .jpg then click Save and it'll bring up a dialogue box that lets you set the compression/quality level. There will be a little checkbox you can use to turn on a preview in the image window itself.
Thats basically what I needed.  Thanks.

---

### Post by zgornel on 2007-03-11
There is a Save for web plugin but I am not aware of either its whereabouts or tech details

---

### Post by P_Badger on 2007-03-11
There's currently a "save for web" option in GIMP 2.3.15 unstable release that works quite nicely. A forum user named "Soc" has put together a .deb package of it and has a link to it somewhere on the forum.

---

### Post by IYY on 2007-03-11
JPG and PNG formats ask for quality whenever you save anyway. To set the number of colours for gif images, simply go to Image > Mode > Indexed.

---

### Post by LepeKaname on 2008-06-01
Hello, I prepared 2 .deb packages for Ubuntu Hardy x86 and amd64 versions.
I did them with checkinstall (with default options), so I hope they work propertly.

You can download it from my site:

[http://www.alepe.com/about_computers/about_linux/save_for_the_web_in_gimp.html]("http://www.alepe.com/about_computers/about_linux/save_for_the_web_in_gimp.html")

Also, you can see some gimp screen-shots to see what is this plugin about.

I hope you find it useful.

---

### Post by Vadi on 2008-10-08
[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

---

### Post by AJB2K3 on 2008-10-08
Using it myself, great plugin for photography forum work especially added to the ufraw plugin.

---

### Post by smartboyathome on 2008-10-08
> **LepeKaname said:**
> Hello, I prepared 2 .deb packages for Ubuntu Hardy x86 and amd64 versions.
I did them with checkinstall (with default options), so I hope they work propertly.

You can download it from my site:

[http://www.alepe.com/about_computers/about_linux/save_for_the_web_in_gimp.html]("http://www.alepe.com/about_computers/about_linux/save_for_the_web_in_gimp.html")

Also, you can see some gimp screen-shots to see what is this plugin about.

I hope you find it useful.

Never use checkinstall to create deb packages, as it doesn't do a very good job with dependencies and the precompiled ones are made specially for your computer (and most likely won't work on other computers).

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by leonbravo on 2009-11-03
try image -> mode -> indexes. radio button web palette.

cheers,

L

---

### Post by haradeep on 2009-12-14
I found in GIMP registry. this may help you. I used this.

link for it is
[http://registry.gimp.org/node/33](http://registry.gimp.org/node/33)

---

### Post by Exodist on 2009-12-14
Thread Necromancy

---

### Post by timjohn7 on 2009-12-14
I always install the Save for Web plugin immediately after upgrading or re-installin the GIMP.  Get it from [www.getdeb.net](www.getdeb.net)

---

### Post by Exodist on 2009-12-14
> **timjohn7 said:**
> I always install the Save for Web plugin immediately after upgrading or re-installin the GIMP.  Get it from [www.getdeb.net]("http://www.getdeb.net")
Is it really necessary? Basic GIMP compresses Jpegs nicely and at a small size. I personally use PNGs for most of my foreground webart because of the clarity, translucency and decent size. I only use Jpegs when the image is large or not needed to be detailed.

---

### Post by timjohn7 on 2009-12-15
> **Exodist said:**
> Is it really necessary? Basic GIMP compresses Jpegs nicely and at a small size. I personally use PNGs for most of my foreground webart because of the clarity, translucency and decent size. I only use Jpegs when the image is large or not needed to be detailed.
Save for Web allows one to strip EXIF data and to interactively reduce jpeg compression while watching the effect on the image.  I'm an artist, so photos of my paintings are my main use for Save for Web and I like to keep a balance between image quality and size.
For general photos etc it may be overkill, sure.

---

### Post by Exodist on 2009-12-15
> **timjohn7 said:**
> Save for Web allows one to strip EXIF data and to interactively reduce jpeg compression while watching the effect on the image.  I'm an artist, so photos of my paintings are my main use for Save for Web and I like to keep a balance between image quality and size.
For general photos etc it may be overkill, sure.
Good Info. 
I wasn't sure what the difference was.

---

### Post by Niva on 2009-12-15
> **Exodist said:**
> Is it really necessary? Basic GIMP compresses Jpegs nicely and at a small size. I personally use PNGs for most of my foreground webart because of the clarity, translucency and decent size. I only use Jpegs when the image is large or not needed to be detailed.

Not necessary, but real nice that the plugin allows resizing and a number of things w/o destroying the original.  Actually I commonly make the mistake in Photoshop of destroying my original after resizing and flattening in order to properly save for web.  

Great plugin!

---

### Post by Exodist on 2009-12-16
> **Niva said:**
> Not necessary, but real nice that the plugin allows resizing and a number of things w/o destroying the original.  Actually I commonly make the mistake in Photoshop of destroying my original after resizing and flattening in order to properly save for web.  

Great plugin!
Ahh yea PS does do that.. I forgot. 
Thank god GIMP doesnt..

---

