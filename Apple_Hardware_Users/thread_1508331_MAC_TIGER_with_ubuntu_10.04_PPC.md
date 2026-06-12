---
title: "MAC TIGER with ubuntu 10.04 PPC"
date: 2010-06-12
forum: Apple Hardware Users
---

### Post by djcmtk on 2010-06-12
Hi guys, I`m new in this fuorum.

I have a MAC G4 AGP with 1GB  RAM PC133, HD 40GB.

I install Ubuntu 10.04 PPC and  MAC oS X Tiger in the same machine.

First install TIGER and after Ubuntu.

All work fine, I can select Boot in Mac or Ununtu, but after update Mac tiger and Ubuntu...

...blank screen. The machine don`t show the boot menu. Only boot in linux, but I have press enter...enter...enter...


How I can rescue the boot menu?

Thanks...

---

### Post by linuxopjemac on 2010-06-13
what is your monitor ?

---

### Post by djcmtk on 2010-06-16
Hi, my monitor is 

PROSYS
Model: S770
15''

Pd: Before I'm selec MAC or Ubutu 10.04...

----------------------
Menu

C= Boot c
L = :Linux
X = Mac

-------------------------

After, update Mac Tiger three or five times....version, java, 5, 6.,8...etc....

...Reboot .....and black screen...I can't write X....only press ENTER, ENTER, ENTERRR...30 seg wait....and,...

..Only boot Linux....

I formated the machine two times.

Thanks...

---

### Post by linuxopjemac on 2010-06-16
Not easy this one. You have a bootloader which is not configured correctly.

Can you get into a command line if you select Linux? Otherwise you have to chroot into your system from a live CD and correct yaboot from there.

Some reading:
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)
[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

