---
title: "Swap partition"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by regbsn on 2008-02-28
Please see laptop specs in signature.

Can Ubunto and Xp share a swap partition? 
If they can...

1. What file format (NTFS, ext2 or ext3)? Why?

2. How do I tell XP and Ubuntu to use a multi-format swap partition.

3. With only 512 RAM, how large should he swap partition be?

If they can't...

1. Should I leave XP swap on XP partition or place it on shared data partition (NTFS) to minimize wasted space and allow for XP swap file to be of variable size.

2. Does Ubuntu require a swap partition? I was going to separate "/ home" and "/" onto their own partitions for easier update...to avoid having to re-setup my Linux environment.

3. Should I leave Ubuntu swap on Ubuntu partition to minimize wasted space and allow for Ubuntu swap file to be of variable size or place it on its own partition?

4. Where should I place each swap file? I hope to have a XP partition, a shared data partition (what file system format?), "/ home" and "/". 

This Laptop is going to be a tester for playing with XP and learning Linux. I can't afford to screw up my primary computer by monkeying around with XP...my wife would kill me!!!!

---

### Post by glennric on 2008-02-28
No, Ubuntu and Windows (any version) can not share swap.  Windows doesn't use a seperate partition for swap, it uses a swap file.  Ubuntu can do that (not with the windows file), but typically uses a swap partition.  I believe the recommended size is about 1/2 of a gig.  When you install Ubuntu you can set up the swap partition.  You can also seperate / and /home on different partitions if you like.  I do and I recommend it.

---

### Post by overdrank on 2008-02-28
HI and to add this link
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Tatty on 2008-02-28
Windows does not use a swap patition, It stores all swap data in a page file which is stored on the XP partition.

**EDIT: Beaten to the reply again! :)**

---

### Post by oedha on 2008-02-28
windows didnt use swap partition...linux yes
for your incoming partition
ntfs partition = windows
ext3 partition = /
ext3 partition = /home
swap partition = swap ( you can set 512MB - 1GB )
or
ntfs partition = windows
ntfs partition = data for both
ext3 partition = /
swap partition = swap
or  ( not really recommended )
ntfs = windows and data
ext3 = /
swap = swap

swap will automatically maintain by linux...you dont have to put anything...you just assign the partition for swap :)
since you have 20GB HD and 9gig is using by windows....it will need extra work for your plan

---

### Post by oedha on 2008-02-28
addition : for / partition....maybe you can assign for up to 5GB :)

---

### Post by regbsn on 2008-02-28
Okay let me...

I have my XP and windows programs down to 7.6 G with 10.7 free space and XP swap at 512MB to conserve space. I have 1.5 to 2 G of Windows programs. Can I place the programs on the shared data partition so that Wine could use them on Linux. I assume that the XP swap has to stay on the XP partition.


Possibilities:
  XP / XP swap partition (only if swap can't be on shared data partition)
  NTFS shared data partition with Windows programs also
  "/" partition
  "/ home" partition
  "Linux Swap partition

  XP/XP swap partition/Windows programs
  NTFS shared data
  "/" partition
  "/ home" partition
  "Linux Swap partition
 
  Why not (just curious)
  XP/XP swap partition/Windows programs/shared data
  "/" partition
  "/ home" partition
  "Linux Swap partition

---

### Post by oedha on 2008-02-28
comment for the last......it will create you 2 data places.....
back to you....do you really need 2 places for your data ?

---

### Post by overdrank on 2008-02-28
Just a thought
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
also more info 
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by regbsn on 2008-02-29
I am still confused! :(
Should I repost with the partitioning question?

---

### Post by regbsn on 2008-02-29
Bump....for fresh ideas:)

---

