---
title: "Macbook 5.5, Maverick, Suspend not working"
date: 2010-10-26
forum: Apple Hardware Users
---

### Post by mzruya on 2010-10-26
Hi, i recently installed ubuntu 10.10 64bit on my macbook 5.5,
everything worked find, till suddenly suspend stopped working, i get the message : " Computer failed to suspend.

Failure was reported as: Cannot suspend"

every time i close the lid of my macbook or select suspend from the menu, 

anyone encounter a similar issue ?

thanks !

---

### Post by linuxopjemac on 2010-10-27
macbook 5,5 or mbp 5,5 ?

---

### Post by o_s on 2010-10-27
Same problem here with Intel Macbook 5,1

---

### Post by Hatsune Miku on 2010-10-28
> **o_s said:**
> Same problem here with Intel Macbook 5,1

Did you give Swap space? The computer will not go into Suspend without Swap Space. Also make sure you have the latest EFI boot code

---

### Post by o_s on 2010-10-28
Yes I have latest boot ROM installed and 2.7 GB swap partition in my system.

Boot ROM Version: MB51.007D.B03
SMC Version: 1.32f8

---

### Post by fhjlx on 2010-10-28
did you install laptop-mode-tools?

apparently when you install laptop-mode-tools it uninstalls pm-utils which is required to suspend I think.

I followed some instructions here to keep laptop-mode-tools installed and reinstall pm-utils : [http://art.ubuntuforums.org/showthread.php?t=1592424](http://art.ubuntuforums.org/showthread.php?t=1592424)

---

### Post by o_s on 2010-10-28
True. I removed laptop-mode-tools and reinstalled pm-utils and suspend is working again.

Bug report related to this issue: 
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)

---

