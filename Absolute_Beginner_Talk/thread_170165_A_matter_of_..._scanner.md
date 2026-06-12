---
title: "A matter of ... scanner"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-05-04
Installing Ubuntu, by mistake due to ..., I've comletely erased xp. Now I'm trying to reinstall everything step by step in Ubuntu. 
I've managed with one fo two printers, but I need now the scanner. I was used to Xp which automatically would "welcome" the new hardware.](*,) 
WHere shal I sart with Ubuntu? I've got a canon Lide 500F. 
I'm loosing myself in the sea of documentation which I find rather difficult](*,)  for me.

Thanks for every kind of help.:)

---

### Post by chriscando on 2006-05-04
Hopefully it already works, try running the program kooka in Applications >Graphics. Does it seem to detect it in there? I find most of the time that my USB devices just work without having to install more drivers (like in windows).

---

### Post by 3rdalbum on 2006-05-04
Kooka isn't included with Ubuntu by default. Have you tried going to XSane and seeing if it automatically detects your scanner?

---

### Post by nalmeth on 2006-05-04
[http://packages.ubuntulinux.org/breezy/graphics/sane](http://packages.ubuntulinux.org/breezy/graphics/sane)
there are other programs out there too.
I think you can scan with the GIMP

---

### Post by Sef on 2006-05-04
Good news.  Sane says it works good.

[http://sane-project.org/cgi-bin/driver.pl?manu=Canon&model=Lide+500F&bus=any&v=&p=]("http://sane-project.org/cgi-bin/driver.pl?manu=Canon&model=Lide+500F&bus=any&v=&p=")

---

### Post by helphope on 2006-05-04
[QUOTE=3rdalbum]Kooka isn't included with Ubuntu by default. Have you tried going to XSane and seeing if it automatically detects your scanner?[/QUOTE]

I got  down to look for xsane, tried it ... and got a  "The scanner is not detected"](*,) .
I also had  a look at the different links of the forum dealing with scanners: but as far as I can see they are not to the point.

---

### Post by Sef on 2006-05-04
Are you using Breezy or Dapper?

---

### Post by helphope on 2006-05-04
[QUOTE=Sef]Are you using Breezy or Dapper?[/QUOTE]

I'm using Breezy.

---

### Post by nalmeth on 2006-05-04
Hopefully this can get you started somewhere:
[https://wiki.ubuntu.com/ScanningHowTo?action=show&redirect=ExtraScannersHowTo](https://wiki.ubuntu.com/ScanningHowTo?action=show&redirect=ExtraScannersHowTo)

---

### Post by tico on 2006-06-17
[QUOTE=Sef]Are you using Breezy or Dapper?[/QUOTE]

I'm using dapper, but it still doesn't work. I had Breezy, I updated using the automatic update system, but I still have the ancient sane (0.97). How could I install a new sane version and make my Lide 500F work?

Thanks a lot.

---

### Post by tico on 2006-06-19
Bump!

---

### Post by tico on 2007-06-17
Is there a way to use the Canon Lide 500F Scanner in Ubuntu? XSane seems not recognize it. Is there another backend that would recognize it?

Thanks a lot.

---

### Post by tico on 2007-06-26
In sane project page it's written:
 0x04a9/0x221f 	unsupported 	GL841 based, to be added to genesys backend

Will this scanner be supported in a near future?

It also says: unsupported means the device is not supported at least by this backend. It may be supported by other backends, however.

Is there another backend that I can try with this scanner. Which one and how (I'm a newbie)?

Thnaks.

---

