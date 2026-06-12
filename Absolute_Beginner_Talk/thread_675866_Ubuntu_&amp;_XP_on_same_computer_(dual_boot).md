---
title: "Ubuntu &amp; XP on same computer (dual boot) ??"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by CPU GUY on 2008-01-23
Hello 

I need a help

I want to install Ubuntu & windows XP on one computer by using dual boot . How I can do that ???

notice : I am using  2 SATA hard disks (RAID 0) does that make any problems ???

by the way what is --- WINE---  and how I can use it

---

### Post by mister_pink on 2008-01-23
Wine is a bit of software that can run some windows applications under linux, but before you worry about that you'll need to install ubuntu! First I suggest you download the live CD iso and burn it to a CD at a low speed (the lowest you can in your burning software).
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Next start up your computer with the disc in the drive - if you end up back in windows you'll need to go into your bios (press del usually as soon as your computer comes on) and look for boot options to set it to boot from CD first. 

When you get to the live CD you can play around and see if you like it. If you decide you want to install you need to create some space for ubuntu. You can do this manually, using the partion editor on the live CD (under System, administration). Just create a big blank space wherever you want it by shrinking another partion. Then start the install and tell it to use the biggest free space. 

Thats the general gist of it, if you have any specific questions ask away!

Edit: The wiki is a great source of info: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by mikeyphi on 2008-01-23
> **CPU GUY said:**
> Hello 

I need a help

I want to install Ubuntu & windows XP on one computer by using dual boot . How I can do that ???

notice : I am using  2 SATA hard disks (RAID 0) does that make any problems ???

by the way what is --- WINE---  and how I can use it


Welcome!!
Have a read here: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
for installation ideas

and here: [https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed](https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed)
for Raid info

and here:[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
for wine

---

### Post by polmir on 2008-01-23
try this link:
[http://ubuntuforums.org/showpost.php?p=3885978&postcount=1]("http://ubuntuforums.org/showpost.php?p=3885978&postcount=1")
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0")

---

### Post by 565Customz on 2008-01-23
run parted magic set up partition space as follows
 /home - ext 3
/          - ext 3
swap    -auto sets
/shared-fat 32 (only if you want to share with windows...can use ntfs with 7.10)

you will need to set up and extended partition after you resize windows if you put it on the same drive as windows....if you put it on the oposite drive just cerate the partitions and voila.

---

### Post by jonabyte on 2008-01-23
I would install xp first though as it will overwrite grub if you install Ubuntu first. I have this setup at work and home and works great for me.

Good luck!

---

### Post by 565Customz on 2008-01-23
+1

---

### Post by Paulmd on 2008-01-23
> **CPU GUY said:**
> Hello 

I need a help

I want to install Ubuntu & windows XP on one computer by using dual boot . How I can do that ???

notice : I am using  2 SATA hard disks (RAID 0) does that make any problems ???

by the way what is --- WINE---  and how I can use it

Just to add, If you have XP installed already, BACK UP YOUR DATA before installing Ubuntu. The process doesn't usually go awry, but it does often enough to make that a prudent step.

---

### Post by dstew on 2008-01-23
I have heard that using the Alternate Install CD will allow you to install Ubuntu directly to a RAID. The regular Live CD will see your disks as separate. There are ways to install to a RAID using the Live CD (see [Fake Raid How-To]("https://help.ubuntu.com/community/FakeRaidHowto")) but it doesn't look easy. I think Gutsy may already have dmraid installed, but I don't know for sure...

---

### Post by CPU GUY on 2008-01-23
[CENTER][COLOR="Blue"][SIZE="5"]Thanks Guys For help I appreciate It[/SIZE][/COLOR] :KS[/CENTER]

---

