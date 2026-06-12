---
title: "Ubuntu making it hard for me to dual boot w/ windowsXP :("
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by shuRe on 2006-11-29
Basically, i have spent hours researching how to dual boot with windows xp. I have read the guid by machiner (i think), but i get stuck at the same place every time. 

When i try to run qtparter it tells me to select my mouse, i select it, it goes back to the prompts, not bringing up qtparter at all.

I noticed it said i had to run some buffer before, so i followed the instructions of putting in the systemrestorecd, pressing f2, then typing fb800 (also tried fb800 notetech), which went ok, got into prompt to run qtparter, the same, nothing happens when i enter my mouse after typing run_qtparter.

If anyone could help with this ultimate noobie question it would be appreciated, otherwise ill just go back to simple windows xp which doesnt give me headache.

---

### Post by Tilex on 2006-11-29
What are you actually trying to do?  You have WinXP installed and want Ubuntu?  You have Ubuntu intalled and want WinXP to dual boot?

You cannot install WinXP after having installed Linux because WinXP wants the total control over your filesystem.  However, if you already have WinXP installed and merely want to install Linux (Ubuntu), simply boot from the ubuntu installation CD and during the installation, it will detect the other operating system already installed on your system (i.e. WinXP) and will do everything that needs to be done in order for you to have two operating systems to coexist on your system (i.e. dual-boot by installing the GRUB boot loader on your filesystem).

---

### Post by Popbot on 2006-11-29
First post ever

Anyway, being new, I'd would also say just try and do it with the ubuntu install disk. If your hard drive is fairly full, defrag it first. You shouldn't need to use the system recover cd, but it is useful if something goes wrong (like what happened to me, I had a error on my drive)

Also, assuming that you have partitioned your drive properly, I've heard you should install GRUB on your linux partition, not your windows partition, otherwise you could get problems with booting up (but nothing that can't be solved with the recovery cd, I believe)

good luck, it's worth it.

---

### Post by bodhi.zazen on 2006-11-29
First, you need to partition your hard drive.

Start in windows. Defragment your HD.

Then boot to Ubuntu, run gparted, resize your windows partiton, make a new partition. You may format it at this time or you can do it later.

Then follow this guide: [Psychocats install guide](http://www.psychocats.net/ubuntu/installing)

FYI:

You can install in any order windows -> Ubuntu or Ubuntu -> windows.

If you install windows last you need to re-install grub.
[Restore Grub](http://doc.gwos.org/index.php/Restore_Grub)

You can also do it from the llive CD:

```
sudo grub
```

This will give you a grub prompt:

grub >

Type:```
root (hd0,1)
setup hd0
```
Where "(hd0,1)" is your Ubuntu partition in "grub speak".

If you do not know this, look in /boot/grub/menu.lst on your Ubuntu partition.

HTH

---

