---
title: "problem booting linux"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by dylan55555 on 2006-04-09
ok i tryed booting linux a whole bunch of times and kept getting one of 2 things to come up and then it wont move or let me do anything here are the 2 things
[URL="http://img482.imageshack.us/my.php?image=linuxproblem0010xn.jpg"]
http://img482.imageshack.us/my.php?image=linuxproblem0010xn.jpg[/URL]
[http://img482.imageshack.us/my.php?image=linuxproblem0034uc.jpg]("http://img482.imageshack.us/my.php?image=linuxproblem0034uc.jpg")


am i doing somthing wrong or is my computer just messed up cuz this is no the first problem i have had with BOIS

---

### Post by dcstar on 2006-04-09
[QUOTE=dylan55555]ok i tryed booting linux a whole bunch of times and kept getting one of 2 things to come up and then it wont move or let me do anything here are the 2 things
[URL="http://img482.imageshack.us/my.php?image=linuxproblem0010xn.jpg"]
http://img482.imageshack.us/my.php?image=linuxproblem0010xn.jpg[/URL]
[http://img482.imageshack.us/my.php?image=linuxproblem0034uc.jpg]("http://img482.imageshack.us/my.php?image=linuxproblem0034uc.jpg")


am i doing somthing wrong or is my computer just messed up cuz this is no the first problem i have had with BOIS[/QUOTE]
Could be many things, a bad CD, bad memory or just a faulty system.

---

### Post by Panhead Bill on 2006-04-09
Does your machine run Ubuntu with the Live CD?

---

### Post by dylan55555 on 2006-04-09
> 	Does your machine run Ubuntu with the Live CD? im trying to geet it to but thats the problem it wont boot

---

### Post by taurus on 2006-04-09
The second picture seems like it is missing "initrd" in your /boot/grub/menu.lst!!!  Boot your machine using the LiveCD and post your /boot/grub/menu.lst here if you don't know how to add an entry for initrd...

---

### Post by dylan55555 on 2006-04-09
^ i have no idea what ur saying. i burned the iso to a cd rw then i went into the boot menu and hit the cd drive, it went into ubuntu and it said push enter to boot. i started to boot then those things came up and i cant do anything but turn it off when they do

---

### Post by taurus on 2006-04-09
First, did you check to see if your download passed the integrity test with md5sum?  Then, make sure you burn it at a slower speed like 4x even though your CD-RW can handle fast burning.  Burning at hight speed can cause Ubuntu to fail to install!!!

---

