---
title: "dual boot problems"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by blaqmarket on 2007-03-04
hi, ive been reading about ubuntu for a little while now and i decided that i wanted to try it, but keep my windows bootable because i have a lot of graphic design work i do and photoshop and illustrator  arent supported in linux as far as i know. so i created a partition for the root and for a swap disc in partition magic and then installed ubuntu to what i thought were those partitions, but now i dont know if thats where it got installed, because after i restarted my computer, i tried windows and it would not load it, but instead would immediately restart my computer. pleease help, i need all of those files in windows, and i cannot access them through ubuntu. i am really hoping someone can get me out of this problem without having to erase all of my files. thank you

---

### Post by catsmasher on 2007-03-04
Put your WinXP disk in and boot. When windows asks to repair or do a fresh install the first time, select install. If there is only minor damage to the file system, you should have another selection to repair a previous install. Remember, do not select repair from the git-go or you will just get the repair console (unless you're good at Win script), select install and see if the second option to do a repair is there. Also, you can look on the net for free download to put on disk  that will boot an XP system and repair it (or buy one on e-bay for $0.99). 
IF worse comes to worse, you can install a fresh XP copy on the partition you made for Ubuntu and snatch up your files and back them up, then redo fresh installs of both OS'.

---

### Post by confused57 on 2007-03-04
> **blaqmarket said:**
> hi, ive been reading about ubuntu for a little while now and i decided that i wanted to try it, but keep my windows bootable because i have a lot of graphic design work i do and photoshop and illustrator  arent supported in linux as far as i know. so i created a partition for the root and for a swap disc in partition magic and then installed ubuntu to what i thought were those partitions, but now i dont know if thats where it got installed, because after i restarted my computer, i tried windows and it would not load it, but instead would immediately restart my computer. pleease help, i need all of those files in windows, and i cannot access them through ubuntu. i am really hoping someone can get me out of this problem without having to erase all of my files. thank you

Here's how to reinstall Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You can use the Ubuntu live cd to show your partitions, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

Partition Magic would be OK to create partitions for Ubuntu, but not to format ext3.
Also, after restoring Windows mbr, you might want to burn a copy of Super Grub Disk(500 kb download), before attempting to reinstall Ubuntu:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
see the link to SGD in the index

---

### Post by blaqmarket on 2007-03-06
ive been long overdue for a windows reinstall, so i followed catsmashers advice and installed a second windows os on a second hd, unhid the windows partition, and backed up everything i thought i had lost (which is all of my graphic design work ive ever done, which would ruin my chances of getting into college if i actually lost it, thank you catsmasher) now im in the process of reformatting my discs and starting from scratch, dual boot the correct way, even though im still really inexperienced with ubuntu. so im wondering where i should start, i have 250 blank gigs and want to have a dual boot system, windows xp for my graphic design work and ubuntu for everything else. whould i partition first orrrr what... im lost. thank you in advance, the ubuntu community is much more generous than any other help forum ive ever visited.

---

### Post by OBnascar on 2007-03-06
First I would download the partitioner **Gparted Live CD** ISO (see my signature). Gparted is very **user friendly**, in fact I believe there is none better.

Set up WinXP on your first partition for installing, then on a second partition you may want to create a storage partition for your important files, in other words another WinXP partition. 

Then make a partition for the Ubuntu install and another one for Linux storage. I would recommend formating your Linux partitions with the **Ext3** file system.

Hope this helps, and good luck......

---

### Post by blaqmarket on 2007-03-06
if i do it that way will i still be able to read all of my files in both ubuntu and winxp? such as music, videos etc without having to have different partitions with different formats? i understand the partition i install linux onto needs to be ex3 i believe, but do all of my files i will use while in linux have to be on an ex3 partition as well?

---

### Post by louieb on 2007-03-06
> **blaqmarket said:**
> if i do it that way will i still be able to read all of my files in both ubuntu and winxp? 
Ubuntu out of the box can read NTFS (a Microsoft file system). You can install write support also. I've never heard of  trouble with it but the software is still in beta. (been in beta several years in fact.) 
Windows programs are out there that allow you to read and write to ext2/ext3 file systems. But if you use one of the other Linux file systems then I don't know of anything that can read or write.
So you can let each system read or write each others data or any combinations of as you see fit.

---

