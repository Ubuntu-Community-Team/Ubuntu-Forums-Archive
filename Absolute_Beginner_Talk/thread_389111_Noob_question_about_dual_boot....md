---
title: "Noob question about dual boot..."
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Hyper-x on 2007-03-20
Hello everyone, I'm new here and also at Linux... and I have a doubt about dual booting Linux and Win XP, here it goes:
I have 2 SATA WD 160gb drives, I have partitioned the first drive and installed WinXP, I want to install Ubuntu on the same HD, my question is, how can I install it on a different partition without erasing Win XP? :confused: (the second drive would be for files and stuff)
I made some research and I couldn't find a straight answer

Thanks for your help!

---

### Post by justleen on 2007-03-20
> **Hyper-x said:**
> Hello everyone, I'm new here and also at Linux... and I have a doubt about dual booting Linux and Win XP, here it goes:
I have 2 SATA WD 160gb drives, I have partitioned the first drive and installed WinXP, I want to install Ubuntu on the same HD, my question is, how can I install it on a different partition without erasing Win XP? :confused: (the second drive would be for files and stuff)
I made some research and I couldn't find a straight answer

Thanks for your help!

the install lets you choose which partition you want to use for Ubuntu. 
It even shows de the partition labels, so if you have named them (name your designated linux drive LINUX or something in windows) you should have no troubles picking the right part.

---

### Post by wpshooter on 2007-03-20
You SHOULD be able to use the paritioning software of the DESKTOP CD to resize the XP partition to make space for the Ubuntu O/S.

It is my understanding that you will probably want to run chkdsk and defragment on the XP O/S about twice **before** attempting to install Ubuntu.

HOWEVER, having said the above, I do NOT recommeding having two different O/Ss on the same computer.  I don't think it is worth the risk.

---

### Post by mikesignguy on 2007-03-20
download GTparted....

the easiest way to do it is to partition the drive three ways....

1 st part is XP

2nd part has a fat32 for viewing from XP and Linux

3rd part is linux

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Hyper-x on 2007-03-20
Thanks for the quick reply, so on the install menu should I choose automatic or the manual edit of the partition? thats the point where I'm stuck, i dont wanna loose my info
thanks

---

### Post by randomdarkness on 2007-03-20
So do you get the option to resize the partition while installing Ubuntu?  I have an existing install of WinXP on my laptop - i don't have the option of installing Ubuntu on another PC at the moment so i would have to dual boot with XP.  The XP install was not put on a specific partition - It made the entire HD an NTFS partition during the initial install.  Can Ubuntu still be installed as a dual boot OS?  If not Is there a way to run Ubuntu from a Bootable CD image without actually having it install on the PC HD? or From a USB Flash drive?

---

### Post by justleen on 2007-03-20
> **Hyper-x said:**
> Thanks for the quick reply, so on the install menu should I choose automatic or the manual edit of the partition? thats the point where I'm stuck, i dont wanna loose my info
thanks

hyper: 
Is your drive already partitioned? As in, do you already have an empty partition for Ubuntu?
If that is the case, you select the pasrtition, and in the setup choose Automatic.

If you dont have a partition free, you will have to resize your XP partition first, to create empty space, as the posters above suggest

---

### Post by justleen on 2007-03-20
And no, ubuntu wont lets you RESIZE a partition during the installation. The OP started with >  .. I have partitioned the first drive and installed WinXP.. 
which to me sugggested that he already had an empty  partition for Unbuntu (ie, he didnt use the full 160 gb for XP)

---

### Post by Hyper-x on 2007-03-20
> **justleen said:**
> hyper: 
Is your drive already partitioned? As in, do you already have an empty partition for Ubuntu?
If that is the case, you select the pasrtition, and in the setup choose Automatic.

If you dont have a partition free, you will have to resize your XP partition first, to create empty space, as the posters above suggest

Well I put my Win Xp on a 25GB partition, and I have the remaining part free but is not formatted and i follow the steps like this [https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")
but i dont get the option to resize the disk :confused:

---

### Post by justleen on 2007-03-20
it wont let you resize. If you dont want to use the remaining space, boot into XP, create e new (fat32) partitio, label it Ubuntu, and run the install. 
you can then select the drive.

Or, as suggested above, use gparted on the live cd, create a partitio, and run the install.

---

### Post by mikesignguy on 2007-03-20
[http://qtparted.sourceforge.net/features.en.html](http://qtparted.sourceforge.net/features.en.html)

see if qtparted works for you, it worked for me,

moved and partiioned it the way i wanted
plus it is easy to use

---

### Post by Hyper-x on 2007-03-20
Ah ok Justleen, thanks for your help, let me try when I get home and Ill post if I have any trouble :)

---

### Post by randomdarkness on 2007-03-21
Here,s the info I get from gpart off the live CD 

HD Size 25.99 GB 
Used    17.21GB
Unused 8.78 GB

Unallocated Size 1.95 GB 

To me it looks as if most of the drive is formatted as NTFS - except for the unallocated space - I would probably have to reinstall XP after repartitioning the HD to dual boot Ubuntu wouldn't I?  

I may just find a used desktop that I have laying around and install it on that to mess with.  

If I have a desktop that has XP on it and the HD is formatted in NTFS - could I run the install from the live cd and use gpart to wipe out the existing XP install and install Ubuntu on the HD in its place? Or do I first have to use some sort of Drive wiping software to eliminate the NTFS partition alltogether before trying to install Ubuntu?  

Some of the questions may seem redundant or a bit lame but I really only have experience with Windows Based OS's to this point and am trying to learn Linux with very little knowledge on the OS ?  Thanks.

---

### Post by mikesignguy on 2007-03-21
[QUOTE=randomdarkness;2331427]Here,s the info I get from gpart off the live CD 

HD Size 25.99 GB 
Used    17.21GB
Unused 8.78 GB

Unallocated Size 1.95 GB 

To me it looks as if most of the drive is formatted as NTFS - except for the unallocated space - I would probably have to reinstall XP after repartitioning the HD to dual boot Ubuntu wouldn't I?  

QTPARTED WILL DO IT

I may just find a used desktop that I have laying around and install it on that to mess with.  

If I have a desktop that has XP on it and the HD is formatted in NTFS - could I run the install from the live cd and use gpart to wipe out the existing XP install and install Ubuntu on the HD in its place? Or do I first have to use some sort of Drive wiping software to eliminate the NTFS partition alltogether before trying to install Ubuntu?  

YES!

Some of the questions may seem redundant or a bit lame but I really only have experience with Windows Based OS's to this point and am trying to learn Linux with very little knowledge on the OS ?  Thanks.

---

### Post by rusty4r on 2007-03-21
Try this guide I think it will explain what you need
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

And like justeen I was thinking you already have empty space for Ubuntu. The installer will let you choose that empty space, partition it and then install Ubuntu on it. Just remember to leave a small space at the end for a swap partition. The guide will show you step by step with screenshots.

---

