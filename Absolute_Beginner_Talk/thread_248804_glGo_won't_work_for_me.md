---
title: "glGo won't work for me"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-09-01
I installed the go (the game) client. Ther debian package is at 
[http://www.pandanet.co.jp/English/glgo/download.html](http://www.pandanet.co.jp/English/glgo/download.html)
(though their server is very slow today).
The deb package installs no problem but when I enter 
glGo 
I get the error message 
> glGo: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
So I uninstalled and intsalled using a shell script form sourceforge
[http://ggo.sourceforge.net/](http://ggo.sourceforge.net/)
This goes through the installation but I still get teh same error message. 
It seems ubuntu has libsdl_ttf-2.0.so.0 with a small sdl.

I downloaded the windows version and it works under wine, but it seems a bit silly to run it this way.

If the debian installer says I have all the dependencies then what's wrong?

---

### Post by wayward on 2006-11-25
Bloch, 

check out this mini-howto: [http://www.ubuntuforums.org/showthread.php?t=302521]("http://www.ubuntuforums.org/showthread.php?t=302521")

---

