---
title: "Installing Ubuntu over Lispire"
date: 2005-05-10
forum: Absolute Beginner Talk
---

### Post by urger on 2005-05-10
I've used linux in various forms for some time now either using live CD's or via remote access.  But I've never actually owned a computer that has Linux installed on it.  I was just given a computer that has Linspire preinstalled.  That said, I dislike Linspire, so after some testing, I've decided to replace it with Ubuntu.  It's downloaded, burned to a CD, but here I face my problem, I have no clue what to do next. Do I have to remove Linspire first? If so, how? Or do I just pop the Ubuntu install CD in and let it ride?
HELP!

---

### Post by shakin on 2005-05-10
[QUOTE=urger]I've used linux in various forms for some time now either using live CD's or via remote access.  But I've never actually owned a computer that has Linux installed on it.  I was just given a computer that has Linspire preinstalled.  That said, I dislike Linspire, so after some testing, I've decided to replace it with Ubuntu.  It's downloaded, burned to a CD, but here I face my problem, I have no clue what to do next. Do I have to remove Linspire first? If so, how? Or do I just pop the Ubuntu install CD in and let it ride?
HELP![/QUOTE]
 Just put the Ubuntu CD in and reboot the computer. The Ubuntu installer will format the drive as needed.

---

### Post by urger on 2005-05-10
Thanks **shakin**.  :grin:  Next time I post it'll be from Ubuntu.

---

### Post by Stormy Eyes on 2005-05-10
[QUOTE=urger]Thanks **shakin**.  :grin:  Next time I post it'll be from Ubuntu.[/QUOTE]

It's probably too late, but make sure to save any files you want to keep before installing Ubuntu.

---

### Post by urger on 2005-05-10
Not to worry, I'm a obsessive-compulsive backup-maker.

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=urger]Thanks **shakin**.  :grin:  Next time I post it'll be from Ubuntu.[/QUOTE]


Good be sure to check ou the ubuntu guide.

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by baslow on 2005-09-15
Will this work in cases where Linspire is installed on a dual-boot system?  Will the Ubuntu install CD automatically alter the GRUB configuration?  Or do I need to do that myself...and in that case, how?

Thanks.

---

### Post by SilentCacophony on 2005-09-15
[QUOTE=baslow]Will this work in cases where Linspire is installed on a dual-boot system?  Will the Ubuntu install CD automatically alter the GRUB configuration?  Or do I need to do that myself...and in that case, how?

Thanks.[/QUOTE]

When you install ubuntu, if you choose to install grub to the mbr, it will normally detect any remaining linux or windows partitions, and place them after your ubuntu choices in the grub menu automatically. It does let you verify that it is correct before it writes grub to disk.

---

