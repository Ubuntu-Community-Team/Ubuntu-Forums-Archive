---
title: "Dual Boot."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Icon41 on 2006-09-10
I want to dual boot, but the problem is I have linux installed as main sstyem and its partition is taking up the whole HD, how would I go about installing windows Xp so it dual boots.

---

### Post by Najand on 2006-09-10
Repartition the waste space on your unsed partitions and then install windows on the new partion. Use [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
To edit  grub after you are done with windows installation.

---

### Post by jorn on 2006-09-10
You have to resize your partition. That's only possible from outside the OS.
Use gparted on your live-cd or even better download the gParted live-cd from the net.That runs in your memory while your hd is unmounted.

---

### Post by slibuntu on 2006-09-10
To the best of my knowledge Windows overwrites the Master Boot Record when it installs, which would prevent you from booting ubuntu. What you'll have to do is 1. back up your ubuntu files, 
2. re format your hard drive, 
3. install Windows 
4. install ubuntu as a dual boot,

For help with step 4, you can check out my blog, i did a post all about exactly how to do that

---

### Post by bulldog on 2006-09-10
> **slibuntu said:**
> To the best of my knowledge Windows overwrites the Master Boot Record when it installs, which would prevent you from booting ubuntu. What you'll have to do is 1. back up your ubuntu files, 
2. re format your hard drive, 
3. install Windows 
4. install ubuntu as a dual boot,

For help with step 4, you can check out my blog, i did a post all about exactly how to do that

Not neccessary to format.
You can install grub after the windows install from the live cd.
Just repartion your drive and install windows.
Then install grub from the live cd on the following manner.

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

Don't forget to alter your menu.lst AND your fstab if neccessary.


That is it. Grub will be installed to the mbr.

---

