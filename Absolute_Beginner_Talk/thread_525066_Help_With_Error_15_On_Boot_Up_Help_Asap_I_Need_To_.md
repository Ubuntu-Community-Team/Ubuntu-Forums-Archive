---
title: "Help With Error 15 On Boot Up Help Asap I Need To Start School"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by spawky on 2007-08-13
Ok I Had Xp And Ubuntu Dual Booted Then I Decided To Take Ubuntu Off And Whn I Did I Rebboted It  Said Loidint Grub Then Error 15 Wtf Does This Meen I Need To Get Back To Xp How Do I Fix This Help Asap

---

### Post by amsterdam on 2007-08-13
I am not an expert but it sounds like grub is still trying to boot linux. probably want to change the default to the windows partition...

---

### Post by spawky on 2007-08-13
how do i do that thansk

---

### Post by Arisna on 2007-08-13
Actually, I don't think you can edit your GRUB configuration anymore since you've gotten rid of Ubuntu.   Your best bet is to boot from Windows XP installation media, access the recovery console, and enter the command "fixmbr".

---

### Post by spawky on 2007-08-13
Well I Dont Have My Xp Instalatian Disk So Is There Any Thing Else I Could Do

---

### Post by spawky on 2007-08-13
Caus Ei Realy Need To Start School

---

### Post by spawky on 2007-08-13
Ok Sorry For Trip But I Realy Need To Start Scool So I Need To Fix This

---

### Post by siralphred on 2007-08-14
try this might be helpful [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by spawky on 2007-08-14
Well I Just Want Too Boot From Xp Thats It

---

### Post by confused57 on 2007-08-14
Here's several methods to install Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Super Grub Disk is probably the easiest method...it's a very small download(5-7 Mb?).

If you don't have access to another computer to burn a copy of SGD, you'll need to reinstall Ubuntu, make a copy...then use SGD to restore your Window's boot.

---

