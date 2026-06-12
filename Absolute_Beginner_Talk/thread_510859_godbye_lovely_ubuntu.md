---
title: "godbye lovely ubuntu"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by youdidntseenothing on 2007-07-27
loved ubuntu, i learnt a frick of things that should be in every os. but, its goodbye for now, hardrive is smaller than a pea. i have windows and i have installed it (so its a dual boot system). how do i get rid of ubuntu+GRUB?
i can get rid of the partition and remake it to a ntfs, but how do i get rid of the mbr, which GRUB sits in? am i doing this right? thankkkkks

---

### Post by AlexenderReez on 2007-07-27
i think there is option to reset mbr in windows cd(i'm using vista,i'm not sure about lower version)...

---

### Post by LuisAugusto on 2007-07-27
> **youdidntseenothing said:**
> loved ubuntu, i learnt a frick of things that should be in every os. but, its goodbye for now, hardrive is smaller than a pea. i have windows and i have installed it (so its a dual boot system). how do i get rid of ubuntu+GRUB?
i can get rid of the partition and remake it to a ntfs, but how do i get rid of the mbr, which GRUB sits in? am i doing this right? thankkkkks

It would be better if you'll say goodbye to Windows :P

---

### Post by tomcheng76 on 2007-07-27
you can simply format the Ubuntu partition in windows
start -> run -> compmgmt.msc
then insert your windows XP, load something and then go to Recovery Console
then fixmbr
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by ugm6hr on 2007-07-27
Have you seen this:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

It will prevent you making a mess of Windows when you remove Ubuntu.

---

### Post by Carlos Santiago on 2007-07-27
Check this:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by ugm6hr on 2007-07-27
> **Carlos Santiago said:**
> Check this:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Didn't I just say that?

---

### Post by youdidntseenothing on 2007-07-27
best and easiest way i found was :
first run compmgmt.msc and format the linux partition
then get fixmbr.exe and put it in c:
then goto cmd, cd c:\ and then C:\> MbrFix /drive 0 fixmbr /yes
worked brilliantly.
thanksguys
dont worry, when i get a bigger harddrive, ubuntu will be there !

---

