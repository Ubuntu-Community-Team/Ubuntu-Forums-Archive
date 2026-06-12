---
title: "[SOLVED] No terminal"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by NinjaZec on 2007-10-15
ok i installed twin view and both monitors are working fine but i cant open terminal
using this tread  [http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)
i just started working in Ubuntu i have 7.04

---

### Post by NinjaZec on 2007-10-15
ok i found someone with the same problem :
[http://ubuntuforums.org/archive/index.php/t-511308.html](http://ubuntuforums.org/archive/index.php/t-511308.html)
i ll try to add composite thing
 but i am not sure how can i use the first thing they told him
sudo nvidia-xconfig --add-argb-glx-visuals    if i cant run terminal

---

### Post by NinjaZec on 2007-10-15
i solved the problem 
you have to add

Section "Extensions"
Option "Composite" "false"
EndSection

at the end of your  xorg.conf 
you can enter it and modify it by pressing alt-f2  then type gksudo nautilus and browse to the file it is in etc/x11/

---

