---
title: "adding to the boot process"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by jtclicker on 2008-02-28
I'm currently trying to use xcalib  to launch a profile to the monitor LUT. I can do it via terminal, but I'd like it to boot up with this pre-done. How do I add (and where!) xcalib /profile path so that it does this in the boot process?

---

### Post by marufaberlin on 2008-02-28
You can add it to the runlevel you boot to. KDE includes a runlevel editor, but otherwise, you might have to mess around with the /etc/init.d/ folder and the /etc/init.* files.

---

### Post by jtclicker on 2008-02-28
Thanks. I'm a total newb at this (total experience of two days!), could you be more specific about which init file? I'm guessing the x11? any idea of what code? Sorry of all this is obvious

---

### Post by marufaberlin on 2008-02-29
Well... Linux has different runlevels:
Runlevel 1 is single user
2 to 5 is multi user
6 is reboot
0 is poweroff.

normally you go to 3 or 5.

There are files that control what processes are started when going to a runlevel:
/etc/rc0.d Run level 0
/etc/rc1.d Run level 1
/etc/rc2.d Run level 2
/etc/rc3.d Run level 3
/etc/rc4.d Run level 4
/etc/rc5.d Run level 5
/etc/rc6.d Run level 6

There is a good tutorial about editing runlevels at [http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html).

---

