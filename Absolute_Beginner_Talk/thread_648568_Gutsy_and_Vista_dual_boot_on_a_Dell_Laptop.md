---
title: "Gutsy and Vista dual boot on a Dell Laptop"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2007-12-23
I've got a Dell E1705 laptop with the following specs:
[LIST]
[*]Intel® Core™ Duo Processor T2400 (1.83GHz/667MHz FSB)
[*]Memory 2GB Shared Dual Channel DDR2 SDRAM at 667MHz
[*]Video - Mobile Intel(R) 945GM Express Chipset Family
[*]Dell Wireless 1390 WLAN Mini-Card
[*]120 gb harddrive - SATA I beleive
[/LIST]

This also has the MediaDirect button that I've heard about some problems with.

I currently use only M$ Vista on this machine, but I want to dual-boot it with Gutsy. Other machines in my home are either dual boot, or Ubuntu alone. 

A couple of questions about adjusting/creating partitions.

[LIST=1]
[*]Should I delete the hidden MediaDirect partition? and how?
[*]How should I re-partition the harddrive? The machine I currently have dual-boot is a desktop that I added a second harddrive to so I didn't need to partition. This computer is a laptop, so using the single harddrive is my only choice.
[*]Does the installation CD for Ubuntu handle partitioning? or do I need a third party tool?
[/LIST]

I don't want to lose data, I will backup the important stuff first of course. I just want to resize the Windows portion of the drive while keeping existing data, and make a 20-30 GB partition for Gutsy.

Thank you in advance for the advice.
Brian

---

### Post by bwhite82 on 2007-12-23
The Live CD handles all that you are asking about. System>Administration>Partitions

---

### Post by JimRaynor on 2007-12-23
im anxiously awaiting my live cd of 7.10 too! I'm also gonna dual boot ubuntu and XP on a dell laptop. Hopefully it goes well! :)

FIRST POST! :KS

---

### Post by bwhite82 on 2007-12-23
Welcome to Ubuntu Jim!

---

### Post by shareMenaPeace on 2007-12-23
hi, i had a nice howto, and importend i think is that you manual partition i did just that on asus dual booting vista and had no problems .. just later i opened a boot administration panel in vista - after this i had to use SUPER GRUB DISC to recover grub boot loader... but as i mentioned teh install wa sflawless... i would keep the media stuff ....

---

### Post by parts-man73 on 2007-12-23
I was doing some more research while waiting for a reply and found this guide

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

It appears that Vista can resize it's own partition, Ubuntu can fill the empty space.

I am just concerned with the MediaDirect aspect now. I never use it, and I've read in other threads that it can destroy partitions if the MediaDirect button on my computer is accidentally pushed after Ubuntu is installed.

For those of you that don't know what it is, MediaDirect loads a scaled down version of windows just for playing various media files, instead of booting your computer to regular windows just to play some music or video files. 

Thanks!
Brian

---

