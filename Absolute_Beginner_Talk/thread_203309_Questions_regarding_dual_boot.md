---
title: "Questions regarding dual boot"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Europa2010AD on 2006-06-25
Greetings.

I installed Ubuntu into Microsoft Virtual PC 2004 (my *real* computer is running WinXP) two days ago.  I've been testing and learning a lot about it -- this is the first time I'm running Linux -- and I really like what it offers.  I like it to the point that I am considering making my system dual boot into Ubuntu and WinXP.  I have a couple of questions I'd like to be answered before I make up my mind though:

1) I have two HDD's.  One can be selected as part of the boot sequence in BIOs (the HDD containing WinXP), and the other cannot.  Now, in order to avoid having Ubuntu screwing up my WinXP partition/HDD (I've read the thread about that...), is it possible that I install Ubuntu into the non-bootable HDD?  Would my bootloader detect it?

2) Both my HDD's are in NTFS.  I know Ubuntu can mount and write to NTFS, but I've read that could somehow mess up your partition/HDD.  So for those of you who have a dual boot system ... how do you guys organise your old files?  Do you just move all your old stuff to your new Ubuntu/Linux partition?

Any help would be much appreciated!

---

### Post by drtvasudevan on 2006-06-25
[QUOTE=Europa2010AD]Greetings.

1) I have two HDD's.  One can be selected as part of the boot sequence in BIOs (the HDD containing WinXP), and the other cannot.  Now, in order to avoid having Ubuntu screwing up my WinXP partition/HDD (I've read the thread about that...), is it possible that I install Ubuntu into the non-bootable HDD?  Would my bootloader detect it?[/QUOTE]

oh yes, you can install it in any hard drive or partition.

> 2) Both my HDD's are in NTFS.  I know Ubuntu can mount and write to NTFS, but I've read that could somehow mess up your partition/HDD.  So for those of you who have a dual boot system ... how do you guys organise your old files?  Do you just move all your old stuff to your new Ubuntu/Linux partition?

i have a multiple boot system
while installing ubuntu will erase the file system in the drive chosen as it has its own file system. mine is reisers
old data is best written to a cd.
if one has a fat32 partition it can be read both by windows as well as linux

as for bootloader:
windows boot loader is not capable of living with linux. it wont detect.
you have to install grub bootloader that comes with dapper.
wither you can install it in mbr (the desktop version will do this step without asking you) or in the partition where you install ubuntu itself if you use a "alternative cd"
in which case you need a third party bootloader like xosl to load it for you.

one can comfortably install grub in mbr and live.
it detects windows and ubuntu and you can chose what to boot.

tv
Any help would be much appreciated

---

### Post by Ptero-4 on 2006-06-25
[QUOTE=Europa2010AD]
Greetings.

I installed Ubuntu into Microsoft Virtual PC 2004 (my *real* computer is running WinXP) two days ago. I've been testing and learning a lot about it -- this is the first time I'm running Linux -- and I really like what it offers. I like it to the point that I am considering making my system dual boot into Ubuntu and WinXP. I have a couple of questions I'd like to be answered before I make up my mind though:
[/QUOTE]
Ohh man. Can you enlighten us telling how you managed to get GNU/Linux installed in M$ V$PC. I (and others around the web) have been trying (and miserably failing) to install ANY NON-M$ OS on that POS PC emulator, all b/c it was rewrote in such a way it intentionally refuses to interoperate with non-M$ software.

> 
1) I have two HDD's. One can be selected as part of the boot sequence in BIOs (the HDD containing WinXP), and the other cannot. Now, in order to avoid having Ubuntu screwing up my WinXP partition/HDD (I've read the thread about that...), is it possible that I install Ubuntu into the non-bootable HDD? Would my bootloader detect it?

Yes it can, that's one of the good things about OSS, it can easily be adapted to any sort of setup the user have.

> 
2) Both my HDD's are in NTFS. I know Ubuntu can mount and write to NTFS, but I've read that could somehow mess up your partition/HDD. So for those of you who have a dual boot system ... how do you guys organise your old files? Do you just move all your old stuff to your new Ubuntu/Linux partition?

If you don't need to access your stuff from Windoze, just move it to your ubuntu partition. If OTOH you need to see your files in Windoze, you'll need to make a FAT32 partition to put the files in. The reason is that although NTF$ write support is there, it's very VERY buggy and unstable.

---

### Post by Europa2010AD on 2006-06-26
Thanks a lot for the quick replies, Ptero-4 and drtvasudevan!

As much as I like Ubuntu, I just realised may be the technology is not mature enough for me to completely switch my daily computing needs to Linux yet.  For example, I found out I cannot synchronise my computer with my smartphone running Windows Pocket PC (Evolution only supports PalmOS).

Since checking emails and synchronisation between my PC and smartphone all within one PIM application is a very important daily routine for me, I guess I'd just have to stick with WinXP for now, and experiment with Ubuntu in my free time.  Unless, of course, there's another way to synchronise my smartphone with Ubuntu  :-k 

[QUOTE=Ptero-4]Ohh man. Can you enlighten us telling how you managed to get GNU/Linux installed in M$ V$PC. I (and others around the web) have been trying (and miserably failing) to install ANY NON-M$ OS on that POS PC emulator, all b/c it was rewrote in such a way it intentionally refuses to interoperate with non-M$ software.[/QUOTE]

I ran into some trouble when I first tried to run Ubuntu in MS VPC too; it would just freeze after the splash screen and filled the screen with false colours.  I later created a new VPC file with 512mb RAM (instead of the "recommended" 128mb) and have been able to run Ubuntu (both from running off the CD and installing it) without a single problem.

Weird, isn't it?  On my other VPC file running WinXP, it only has the "recommended" 128mb RAM.  One would think a Linux distro should run fine with just as much RAM!

---

