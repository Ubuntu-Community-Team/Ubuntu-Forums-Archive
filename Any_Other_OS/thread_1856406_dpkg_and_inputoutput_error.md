---
title: "dpkg and input/output error"
date: 2011-10-08
forum: Any Other OS
---

### Post by kimara on 2011-10-08
Hi! 
I'm running debian (arm) under android (chroot). Phone rebooted itself while upgrading and now it gives me problems and 'apt-get upgrade' doesn't work. It says I need to run 'sudo dpkg --configure -a' but it gives me error message: 

dpkg: error: failed to open package info file '/var/lib/dpkg/updates/0011' for reading: Input/output error. 

And it won't let me to remove or move the file (0011).

How I can get this back on track once again?

Thanks for help 
Kimmo

---

### Post by raja.genupula on 2011-10-08
hey look at this 
[http://ubuntuforums.org/showthread.php?t=1644026](http://ubuntuforums.org/showthread.php?t=1644026)

---

### Post by matt_symes on 2011-10-08
Hi

> **kimara said:**
> Hi! 
I'm running debian (arm) under android (chroot). Phone rebooted itself while upgrading and now it gives me problems and 'apt-get upgrade' doesn't work. It says I need to run 'sudo dpkg --configure -a' but it gives me error message: 

dpkg: error: failed to open package info file '/var/lib/dpkg/updates/0011' for reading: Input/output error. 

And it won't let me to remove or move the file (0011).

How I can get this back on track once again?

Thanks for help 
Kimmo

It sounds like filing system corruption although it may be physical damage.  

Try fsck.

If that does not work you can try to delete the file using its inode and debugfs.

Hello raja. I hope your festival was good. Good to see you back.

Kind regards

---

### Post by kimara on 2011-10-08
Problem solved, I just installed debian again, or just moved the new image on a sdcard again. 
[http://www.nerd65536.com/2011/01/how-to-instal-debian-or-ubuntu-in.html]("http://www.nerd65536.com/2011/01/how-to-instal-debian-or-ubuntu-in.html")

---

