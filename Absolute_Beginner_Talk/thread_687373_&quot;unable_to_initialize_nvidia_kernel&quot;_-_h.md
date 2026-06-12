---
title: "&quot;unable to initialize nvidia kernel&quot; - help!"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by flowevd on 2008-02-04
hi

i've just installed ubuntu for the first time on my dell m1330 and i'm an absolute beginner.

i tried to install and download the newest drivers for my videocard (geforce 8400M GS) from the nvidia site. research tells me this might not have been a good idea but i did it anyway.

i followed a guide - which i can't find now - telling me how to install it, first of all downloading some kind of compiling package and then going to a $ prompt and  stopping the gdm so the drivers could install. all went well. at one point the nvidia software tried to download some kind of kernel from the nvidia website but couldn't. then it decided to rebuild the kernel. i thought this sounded fine and sort of exciting so i let it.

since then i have rebooted and got an

"[EE] cannot initialize nvidia kernel"

error. now i'm stuck with the $ prompt and I'm lost... lost....

can i go back to the old 'restricted drivers' driver? or can i make the nvidia one work?

please help.
thanks.

---

### Post by flowevd on 2008-02-04
ah

i found an answer at
[http://ubuntuforums.org/archive/index.php/t-552435.html](http://ubuntuforums.org/archive/index.php/t-552435.html)

(using rc.local to run modprobe.)

---

