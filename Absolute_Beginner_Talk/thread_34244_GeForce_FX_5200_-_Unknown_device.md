---
title: "GeForce FX 5200 - Unknown device?"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by Edmund Hon on 2005-05-14
I just have Ubuntu installed, and followed the instructions on ubuntuguide.org to install the Nvidia drivers. but when I goto the device manager it is showing my FX5200 as an unknown device (see attached pic). What should I do now?

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=Edmund Hon]I just have Ubuntu installed, and followed the instructions on ubuntuguide.org to install the Nvidia drivers. but when I goto the device manager it is showing my FX5200 as an unknown device (see attached pic). What should I do now?[/QUOTE]


Unlike windows, the applications in Ubuntu don't always tell teh state of things. DO you see a Nvidia logo when you login?

---

### Post by mstralka on 2005-05-14
I have an FX 5500 and I got Ubuntu to recognize it after a lot of work.  I had to make some changes to pci.ids, among other things.  See my post here [http://ubuntuforums.org/showthread.php?t=33142](http://ubuntuforums.org/showthread.php?t=33142)

---

### Post by Edmund Hon on 2005-05-14
[QUOTE=poofyhairguy]Unlike windows, the applications in Ubuntu don't always tell teh state of things. DO you see a Nvidia logo when you login?[/QUOTE]

I do get the Nvidia logo during login. However, I'm not sure if it is fully working or not. Do I have to get the driver from Nvidia?

My main concern is I couldn't get a freeware flight sim game working. It is called YSflight. The link is:
[http://homepage3.nifty.com/ysflight/frmindexe.html](http://homepage3.nifty.com/ysflight/frmindexe.html)
or the direct download link for the linux version:
[http://my.vector.co.jp/servlet/System.FileDownload/download/ftp/0/364600/pack/unix/game/sport/ysflight.tar.gz](http://my.vector.co.jp/servlet/System.FileDownload/download/ftp/0/364600/pack/unix/game/sport/ysflight.tar.gz)

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=Edmund Hon]I do get the Nvidia logo during login. However, I'm not sure if it is fully working or not.[/QUOTE]

Congrats then. Its working. That system tool needs a little more development.

[QUOTE=Edmund Hon]
My main concern is I couldn't get a freeware flight sim game working. It is called YSflight. The link is:
[http://homepage3.nifty.com/ysflight/frmindexe.html](http://homepage3.nifty.com/ysflight/frmindexe.html)
or the direct download link for the linux version:
[http://my.vector.co.jp/servlet/System.FileDownload/download/ftp/0/364600/pack/unix/game/sport/ysflight.tar.gz](http://my.vector.co.jp/servlet/System.FileDownload/download/ftp/0/364600/pack/unix/game/sport/ysflight.tar.gz)[/QUOTE]


It might be a dependancy issue. the card works...

This:

[http://www.flightgear.org/](http://www.flightgear.org/)

Flight Simulator has already been packaged to work with Ubuntu. If you have the Universe enabled, then all you have to do is:

sudo apt-get flightgear

---

