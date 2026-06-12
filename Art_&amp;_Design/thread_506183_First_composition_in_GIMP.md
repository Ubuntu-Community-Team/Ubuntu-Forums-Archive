---
title: "First composition in GIMP"
date: 2007-07-21
forum: Art &amp; Design
---

### Post by Chymera on 2007-07-21
Well here goes, a wallpaper i made in gimp, with my logo on it. 
I initially wanted to use the ubuntu logo, but when i discovered that my path logo which i made in ps can also be opened with gimp i thought ill just use my own.

[http://i16.tinypic.com/4rb2izd.jpg](http://i16.tinypic.com/4rb2izd.jpg)

and i find it integrates quite nicely into my desktop 

[http://i17.tinypic.com/6hcpnk6.png](http://i17.tinypic.com/6hcpnk6.png)

---

### Post by smartboyathome on 2007-07-22
Awesome! Would you mind sharing how you got the satin effect?

---

### Post by Chymera on 2007-07-23
1) lots of gradients via "difference"
2)gaussian blur
3)edge detection
4)invert
5)layer adjustment to make it less bright
6)gaussian blurr, so u get rid of the sharp contours resulted in (5)
--6)new layer, fill with a bright shade of gray
--7)noise (scatter rgb, monochrome)
--8)wind (diagonal, lower left to upper right)
--9)displace (use first layer as source and dont make the displacement too big)
--10)layer mode to overlay or soft light
--11)[colorize]

If you plan to make a 500x500 image, make a bigger one (600x600) and crop the size you want out of it, since a certain part of the image, towards the boundaries, will become unusable after (9)

---

### Post by stormyblueyz on 2007-07-23
Excellent!!

Would you mind explaining to me (or linking me to a page that can) how to get the bloody program to install correctly in Ubuntu Fiesty?  :D

---

### Post by kperkins on 2007-07-23
Open up synaptic, search for Gimp, install.  Actually it should already be installed.

---

