---
title: "installing ubuntu"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by nevadaman on 2007-04-23
I have a second hard drive (200GB) that I have been using for storing photos, movies and such. Can I install ubuntu on this hard drive without loosing my info? Does the HD need to be partitioned? Will I have problems booting from ubuntu with windows XP still on my original hard drive? I am new at this and need help. I just know WIN XP is no longer my friend  :confused:

---

### Post by atbnet on 2007-04-23
You'll need to partition it since XP uses NTFS and ubuntu uses ext3. Grub will allow you to pick what you want to boot to so you can pick XP or ubuntu.

---

### Post by LaurelLynn on 2007-04-23
Dear nevadaman,

If you choose to use ¨manual partitioning¨ during installation, the partitioning software has the ability to resize partitions. You select the partion and hit the right mouse button. On the popup menu is a ¨resize/move¨ option.  Be advised, anytime you change the size of a partition you run the risk of loosing whatever is on it. 

There is a good chance that the data on the disk is worth far more than the cost of a third harddrive, and possibly a USB enclosure. Purchasing that would allow you to remove the drive with your stuff, put it somewhere safe, put in the new drive (with the same Master/Slave settings).  Disconnect the power to your XP drive (so it can´t be harmed). And install Ubuntu with an extra NTFS (Windows) partition you can copy your pics and movies to when your done. Then you plug the power back in for the first drive and use the bios menu to pick which os to boot (hit the function key for the boot menu, usually F10 or F12).  If you get a USB enclosure, that leaves you with a backup external drive (which everyone should have).

**If you do want to resize**  you need to defragment the disk first in windows, because only free space at the end of the disk can be used.

---

### Post by nevadaman on 2007-04-28
Thank you for the response to my question. Being new to installing OS's I am unsure just what partitions do and how they work. I have been using WinXP and it is on my original hard drive. According to my "system" I have 992 MB ram. my new hard drive has 175GB of free space remaining. I am using 14.1 GB. what more do I need to install Ubuntu?

---

### Post by mactechy on 2007-04-28
a partition is basically like seperating your HD into fractions, defragment your HD, then tell UB to use free space at the end of the drive, when it asks you how much space, that is how much you will have for windows, so do the math to figure out how much you want to use!

---

### Post by deadgobby on 2007-04-28
If your hard drive is NTFS and you have feisty or Ubie 7.04. You can install using dual boot method and Ubie will ask you how much of the HD you want for each O/S. You can go 50/50 if you like. Please do run the live CD portion before installing. If the live CD does not run or other problems. There may be some hills to climb. There is ways to mount the windows area of the hard drive so you can read it while running linux and vis versa.
Gobby

---

### Post by nevadaman on 2007-04-30
Thanks for comeback, deadgobby, but I guess I didn't input enough inf0.  I do not want to have 2 OS's on one hard drive. I have a second hard drive that I was using for storage only. Now I want to install Ubuntu as another OS on the second HD, but I don't want to lose my movies and pictures, etc that I have stored. I am unsure how to go about it.

---

### Post by zvacet on 2007-04-30
During installation use manual way of partition.That way you will see your ntfs and free space left.Of course you will choose free space to install your Ubuntu.After that this is basic partitions you need

1. root =10GB                    mountpoint  /
2.home =rest of free space exept        mountpoint  /home
3.swap=2xRAM

you can add more partitions if you need it but that is another story

for how to install on two drives look here

[http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives]("http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives")

---

