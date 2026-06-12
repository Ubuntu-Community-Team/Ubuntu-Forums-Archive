---
title: "can i download regular fonts?"
date: 2011-01-31
forum: Art &amp; Design
---

### Post by rapidvictory13 on 2011-01-31
Can I download fonts from any random website like with windows. and still be able to use them in gimp or open office? And if so how can Ido this?  Thanks in advance!

---

### Post by Cloudkookoo on 2011-01-31
if you mean .ttf files then yes, you can use them, download the font and put it in you /home/yourusername/.fonts

not sure if you need to also install it to /.gimp-2.6/fonts folder to get it working in Gimp. Hope I helped.

---

### Post by BcRich on 2011-02-02
hi rapid victory 13



> **Installing downloaded fonts in Ubuntu 10.04 LTS**

   Open the folder where you have downloaded the font file.  
 Double click on the font file to open it. This opens a font viewer window. 
 On the right there is a button, "Install Font".  Click on it. 
 Wait until the button turns to greyed out "Installed". 
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

this also works for me (if you don't mind using terminal)
```
gksu nautilus /usr/share/fonts/truetype

```
this opens fonts dir in which i create a new dir for my downloaded fonts, copy my new fonts into that dir. then 

```
sudo fc-cache -f -v

```

this recreates the fonts cache. I can use any of these fonts in GIMP, Inkscape, Open Office etc....

---

### Post by ssam on 2011-02-03
you can also install by double-clicking the font file.

---

### Post by joinvert on 2011-02-03
Download the free fonts 
[www.webpagefonts.com]("http://www.webpagefonts.com")

---

