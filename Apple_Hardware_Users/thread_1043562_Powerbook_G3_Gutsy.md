---
title: "Powerbook G3 Gutsy"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by xg43x on 2009-01-18
Hi. I spent much of last nite searching my issue trying to install 7.10 Xubuntu on a powerbook g3(firewire) and I could not find out how to get past the "unable to detect a cd-rom" screen. Has anyone had success installing 7.10 on a powerbook g3?

---

### Post by xg43x on 2009-01-18
I found this thread [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904) but the "modprobe ide-scsi" did not work.

---

### Post by stream303 on 2009-01-19
Ah, that is because you need the fix for Gutsy 7.10:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

In this case, you need to modprobe *ide-core* rather than ide-scsi.

It is very easy to get the crossed up.  But it is a drag to even have to do this.  If it drives you crazy, know that Debian "stable" or "Lenny" has no such problems. :)

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

---

