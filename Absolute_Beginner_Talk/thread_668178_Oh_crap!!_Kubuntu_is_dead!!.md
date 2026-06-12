---
title: "Oh crap!! Kubuntu is dead!!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Lord DarkPat on 2008-01-15
oh no!!! I was doing my work, and then I got enticed by the desktop cube effect and the fact that I couldn't use it cuz I didn't have XGL. So, I installed it and it drastically slowed down my comp, but desk cube worked. So I uninstalled it, and did a apt-get clean. Ok, then I tried to install superkaramba, and it gives this stupid error from dpkg, saying that some info list file hasn't been found in "/usr/var/???" don't know the exact path, and so, I try to reboot, it freezes, hard reboot, then fsck, then it turns on, I try to run Konsole, bam!! it freezes again!! What do I do???

---

### Post by SunnyRabbiera on 2008-01-15
well try booting into safe mode and see if you can use sudo apt-get ubuntu-desktop.
this will install gnome and maybe replace KDM with GDM but maybe it will help you see what went wrong if you choose a gnome session.

---

### Post by Lord DarkPat on 2008-01-15
I can't install/remove anything!!

---

### Post by SunnyRabbiera on 2008-01-15
no, I dont mean using add/remove apps or anything of that sort.
do a reboot and once grub starts loading press your esc key and you will see the boot options,
from here boot into the safe move and try as I suggested.

---

