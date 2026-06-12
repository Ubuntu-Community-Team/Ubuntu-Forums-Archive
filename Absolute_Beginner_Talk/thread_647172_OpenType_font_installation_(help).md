---
title: "OpenType font installation (help)"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-12-22
I'm trying to install an OpenType font ([http://www.josbuivenga.demon.nl/anivers.html](http://www.josbuivenga.demon.nl/anivers.html)), but I'm having troubles. I dropped the .otf inside my /usr/share/fonts folder, but it doesn't appear in any of my programs, even after restarting them. Can someone help?

---

### Post by forestpixie on 2007-12-22
Firstly did you update the font cache ```
sudo fc-cache -f
```
I was a bit involved in a thread yesterday with the same problem - apparently the upshot is a lot of programs won't use them

[http://ubuntuforums.org/showpost.php?p=3986505&postcount=19](http://ubuntuforums.org/showpost.php?p=3986505&postcount=19)

this was the thread [http://ubuntuforums.org/showthread.php?t=645363](http://ubuntuforums.org/showthread.php?t=645363)

They do work in kword, but not abiword or openoffice it seems

---

### Post by alecwh on 2007-12-22
Got it working - thank you!

---

### Post by forestpixie on 2007-12-22
ok, cool - can you mark thread please

---

