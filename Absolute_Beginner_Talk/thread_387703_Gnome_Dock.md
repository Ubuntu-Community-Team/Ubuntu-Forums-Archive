---
title: "Gnome Dock"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-03-18
I can't get gnome dock working, as when I follow this tutorial,

[http://ubuntuforums.org/showthread.php?t=302570]("http://ubuntuforums.org/showthread.php?t=302570")

i get this error:

ajeffreys@ajeffreys-laptop:~$ ./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
bash: ./configure: No such file or directory
ajeffreys@ajeffreys-laptop:~$ 
 
Please help
Thankyou,

Ajeffreys

---

### Post by kwaanens on 2007-03-18
You have to first unpack cairo, then cd to the unpacked directory.

./configure means the file configure in your present dir.

---

