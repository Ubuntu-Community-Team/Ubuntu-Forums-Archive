---
title: "Windows"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by MAINB on 2007-09-18
Hi 
I am brand new to Linux and want to know how easy it is to install along side windows XP

---

### Post by quinnten83 on 2007-09-18
very!

---

### Post by buzzmandt on 2007-09-18
do your research tho, one wrong selection and windows is gone
it's very easy to install a dual boot system just don't go into it blind

---

### Post by darren1270 on 2007-09-18
> **quinnten83 said:**
> very!


Seconded!!!!

Oh and when you do your research..... defrag degrag defrag!!!!

---

### Post by philinux on 2007-09-18
Get a second hard drive they are so cheap now and really easy to install. Then you dont have to mess with partitioning. 
Handy also for backing up your data.

---

### Post by PmDematagoda on 2007-09-18
Very easy, I didn't have to do almost any research at all.

---

### Post by Overbyte on 2007-09-18
It's easy. You won't regret it. :)
Use the LiveCD to make it as user-friendly and painless as possible. The ones you get for free from Canonical are the LiveCDs. You won't have problems with that.

If you won't dual-boot (Ubuntu-only)...the general process will be...
1. Backup
2. Pop CD
3. Boot from CD
4. Follow the easy-to-follow instructions :lolflag:
5. Install
6. Find drivers, packages, repositories

If you will dual-boot XP and Ubuntu
1. Backup
2. Wipe all your partitions
3. Create 2 or more partitions (cleanest approach, at least for XP and Ubuntu)
4. Install XP on 1 partition
5. Install Ubuntu on other partition
6. Mess around with something called GRUB* :)
7. Pray both OSes boot.
8. Get 'em drivers and packages

* usually happens when you have SATA drives in the box. An all IDE drive setup is the best, worry-free setup for making dual-boots effortless.

In spite of all that, Ubuntu is really easy to install. You just need to learn a whole lot of terms (and a new way of using the computer) ;)
Go for it.

---

### Post by meborc on 2007-09-18
easy as a nuclear fusion :)

NO NEED TO WIPE THE DRIVE AS INSTRUCTED IN THE PREVIOUS POST!

1) boot to windows and defrag... MANY times... you want to be sure you have empty space in the end of the drive... also note how big is the empty space
2) boot ubuntu cd, go through installation until the partitioning stage... choose MANUAL partitioning
3) now you will see the win partition... resize it to be smaller... but still big enough for all the data what you had in the win partition
4) now click on the EMPTY SPACE you have created... and choose AUTOMATICALLY PARTITION EMPTY SPACE (or similar)..
5) yes, yes, next, next
6) done

not very scary... just be sure to back up all important data JUST IN CASE you mix something up
:)

---

### Post by buzzmandt on 2007-09-18
> 6. Mess around with something called GRUB* 
shouldn't be any messing around with grub, i've dual booted many pc's and never had to "mess" with grub

and i second the "get another hard drive" makes it much easier and less prone to errors during resizing hd

---

### Post by PmDematagoda on 2007-09-18
> **Overbyte said:**
> 
* usually happens when you have SATA drives in the box. An all IDE drive setup is the best, worry-free setup for making dual-boots effortless.

Go for it.


Not exactly, I have an all SATA setup and I didn't face any problems installing XP and Ubuntu together.

The 2 SATA drives being one 80Gb Maxtor and a 200Gb Samsung which obviously contains Ubuntu.:) 

By the way you can simplify the dual-booting process by having two hard drives instead of one.

---

### Post by expatCM on 2007-09-18
Why not watch a movie .....   at the time this helped me out a lot ... ok the version is now not the latest but it is close enough...

[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+dual+boot&total=19&start=0&num=100&so=0&type=search&plindex=0](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+dual+boot&total=19&start=0&num=100&so=0&type=search&plindex=0)

---

### Post by Overbyte on 2007-09-19
[QUOTE=meborc]NO NEED TO WIPE THE DRIVE AS INSTRUCTED IN THE PREVIOUS POST![/QUOTE]

Sure you can move around the partitions and stuff, but starting from scratch and getting it right the first time has that "clean factor", although everyone has their own strategies for this and it's just a suggestion.

[quote=buzzmandt]shouldn't be any messing around with grub, i've dual booted many pc's and never had to "mess" with grub[/quote]

[quote=PmDematagoda]Not exactly, I have an all SATA setup and I didn't face any problems installing XP and Ubuntu together.[/quote]

I have an IDE/SATA mix of drives (with the occasional drive plugged into the FireWire port). Judging from installing many OSes (feisty, dapper, xp, vista, 2003, opensuse) into both IDE and SATA drives, them bootloaders don't like lot's of drives being of different interfaces all crammed into one box.

[thread=542030][COLOR="orange"]Like here.[/COLOR][/thread]
[thread=46003][Color="orange"]And here.[/color][/thread] :)

---

### Post by PmDematagoda on 2007-09-19
Different speeds between IDE and SATA along with different protocols and write methods and whatnot must be the culprits in confusing boot loaders.:)

---

### Post by dptxp on 2007-09-19
To OP:

If you post your hardware details, especially on HDD on RAM, you will get detailed replies good enough for you.

---

