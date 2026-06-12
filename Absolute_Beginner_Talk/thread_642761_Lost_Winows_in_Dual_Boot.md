---
title: "Lost Winows in Dual Boot"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by tweaked on 2007-12-17
Installed 7.10 on a partition next to XP. Windows will not boot now, says it can't autocheck and then a error flashes on the blue screen. Tried to reinstall xp but it shows my XP partition as an OS/2 MAN and that I need to format. 
While booted into Ubuntu, I can read the files just fine and so will Windows(dos?) under system recovery.

Am I hosed?

---

### Post by shadow-of-sin on 2007-12-17
Try using Super Grub Disk to boot into windows:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by cmo220 on 2007-12-17
Super Grub Disk worked great for me.

---

### Post by logos34 on 2007-12-17
have you tried chkdisk from the windows install cd?

hit 'R' for recovery console and then do

> chkdsk /r

> Tried to reinstall xp but it shows my XP partition as an OS/2 MAN and that I need to format
try deleting the partition first with gparted in ubuntu

---

### Post by Herman on 2007-12-18
>  Windows will not boot now, says it can't autocheck and then a error flashes on the blue screen Did you mean:"[                                      autocheck program not found - skipping autocheck]("http://users.bigpond.net.au/hermanzone/p15.htm#autocheck_program_not_found_-_skipping")." ?

                                       This is usually just an error in editing your boot.ini file in Windows.
Check your Windows boot.ini file and make sure you have the correct partition numbers entered. 

Regards, Herman :)

---

### Post by kenan6346 on 2007-12-18
PM me if you need data recovery help.

---

