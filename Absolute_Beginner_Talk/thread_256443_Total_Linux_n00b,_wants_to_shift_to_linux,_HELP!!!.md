---
title: "Total Linux n00b, wants to shift to linux, HELP!!!"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by ChesterBlack on 2006-09-13
I'm a total linux noob, got my free ubuntu 6.06 LTS cd 2 days ago so after playing with the live cd for 2 days now i wanna install it.

Heres what i have :
80 gb pata hdd, with win xp installed & all partitions are NTFS

What i want :
xp + ubuntu dual boot

so here goes the questions :
Pre-Installation :
1. how much space i should free up?
2. should i resize the partitions in windows itself by using some Disk management software or do it with ubuntu setup (at the tme of installation)?
3. i don't wanna lose my data so can anyone tell me how can i install it safely, without hasstles
4. if after the dual boot windows corrupt and i reinstall it, (i know grub will go and ubuntu will stop working) how to fix that thing?

Post-Installation :
1. after installation i heard that linux just shows up command line, if thats true how can i switch to the graphical mode?
2. in live cd i was unable to mount my partitions, will that remain the same in full installation too, if not how?
3. will i be able to play mp3s
4. how can i configure my dialup modem in linux, i have got its drivers for linux and i've also got few linux apps still no clue how to install an app in linux.

thanks in advance for your help, i know the reply will be a bit big but i'm sure some kind mate will help.

---

### Post by Jussi Kukkonen on 2006-09-13
Pre-install questions answered here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
(personally I'd resize ntfs partitions in windows, but the ubuntu installer should now be able to do it...)

> 1. after installation i heard that linux just shows up command line, if thats true how can i switch to the graphical mode?

Not true
> 2. in live cd i was unable to mount my partitions, will that remain the same in full installation too, if not how?

Depends on your partitions. FAT is ok, NTFS is read-only (with included tools).

> 3. will i be able to play mp3s
Yes, search for restricted formats in the wiki.
> 
4. how can i configure my dialup modem in linux, i have got its drivers for linux and i've also got few linux apps still no clue how to install an app in linux.
Installing new software is a subject you should spend some time to get accustomed with. The debian/ubuntu way of installin stuff is way better, in my opinion, than anything else I've seen, butyou've got to understand it...
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Qrk on 2006-09-13
1,2,3) You just need to defrag windows first. Ubuntu comes with its own partitioner.
4) there are several ways... but it is a rare occurence. The easiest way is to get an XP recovery cd and type /fixmbr

1) It doesn't, but if it did, you'd type "startx"
2) Most should mount automagically, you can specify where you want each parition mounted during the install. If not, see [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)
3) not out of the box. Please see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
4) Please see [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

