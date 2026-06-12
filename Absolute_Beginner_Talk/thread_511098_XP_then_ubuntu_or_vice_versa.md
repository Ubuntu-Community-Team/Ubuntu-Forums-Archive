---
title: "XP then ubuntu or vice versa?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by climater on 2007-07-27
Hello,

I have a blank hard drive on which I want to set up a dual boot. My question is, is it better to install Windows XP (I believe the license will still work on the new blank hdd) first then ubuntu or vice versa?

Thank you very much!
David

---

### Post by Majorix on 2007-07-27
First XP then Ubuntu. That's how they do it.

---

### Post by dannyboy79 on 2007-07-27
always Winbloz first as it doesn't like sharing the MBR. (master boot record) Just use hte XP cd to create a new partition how ever big you want windows partition to be, then do it's install. then when it's done and you know xp works, then bootup the ubuntu livecd, then on the desktop, chose Install, then it's up to you whether you want to manually partition (that's what I always do) or chose the auto partitioning which may then want to shrink the partition you just made for windowsxp, it'll work and leave xp alone, but it may make that partition smaller. then chose to install grub onto the master boot record of you main hard drive (the one that contains both os's), Ubuntu will add XP boot option to grub for you, the finish up the install and YOU DID IT. Take er for a spin.

---

### Post by lbyrd33 on 2007-07-27
It is much easier to install windows first and then ubuntu. You can install windows on the entire hard drive and then resize the windows partition using a program called partition magic for windows. After that, install ubuntu in the free space that you just made available and it will take care of the dual boot by recognizing that you have windows on another partition. After installation, the grub boot loader will allow you to choose which os you want to run.

---

### Post by eentonig on 2007-07-27
> **lbyrd33 said:**
> ... You can install windows on the entire hard drive and then resize the windows partition using a program called partition magic for windows.....

Resizing a partition will always give you the risk of data-corruption. Ok, chances are limited to this actually happening. But why would you want to use this road, if you have a clean disk to begin with? just size your partition the way you want it at the end from the start on.

---

### Post by Rocket2DMn on 2007-07-27
I agree, partition ahead of time if you can, but if you don't install windows on the whole drive, then use the LiiveCD to shrink the NTFS partition.  You may want to defrag windows before installing Ubuntu, even if it is a fresh install - this will try and push all the files to the front of the disk, leaving the back part open for Ubuntu.

---

### Post by AHumanUser on 2007-07-27
Not long ago I would have adviced to give 70% of the disc to Windows and 30% to Linux.
Nowadays I advice You vice-versa: give 70% to Linux and 30% to Windows - You won't be dissappointed to add more space to a real high performance OS like GNU/Linux.

In the long run You will give up the 30% of Redmond-OS and use it for Linux instead.

Best wishes
A Human User

---

### Post by dannyboy79 on 2007-07-27
> **eentonig said:**
> Resizing a partition will always give you the risk of data-corruption. Ok, chances are limited to this actually happening. But why would you want to use this road, if you have a clean disk to begin with? just size your partition the way you want it at the end from the start on.

right on, you can create any size you'd like within xp's cd installer. Why would a person create a huge one just to shrink it down????? Also, if you do already have 1 large partiiton, Ubuntu's installer can and DOES properly shrink NTFS partitions WITHOUT data corruption. It's been tested and has worked since Dapper (when I joined the scene)

---

### Post by Bachstelze on 2007-07-27
> **dannyboy79 said:**
> Ubuntu's installer can and DOES properly shrink NTFS partitions WITHOUT data corruption. It's been tested and has worked since Dapper (when I joined the scene)

Yes but there's always the risk of power failure or other problems during the shrinking that will leave the filesystem unreadable. Better avoid it if you can.

---

### Post by MQMike on 2007-07-27
No question -- for easy of setting up and maintaining your dual boot setup, Windows XP first, on (hd0, 0) (the first hard drive, the first partition, numbering starts of zero for the bootloader GRUB).

Should you need it, here's some tips on the booting logic:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by lbyrd33 on 2007-07-27
> **eentonig said:**
> Resizing a partition will always give you the risk of data-corruption. Ok, chances are limited to this actually happening. But why would you want to use this road, if you have a clean disk to begin with? just size your partition the way you want it at the end from the start on.

Thats my fault, for some reason or another I thought xp didnt give you the option of installing to a particular partition; it would just take over the entire drive.

---

