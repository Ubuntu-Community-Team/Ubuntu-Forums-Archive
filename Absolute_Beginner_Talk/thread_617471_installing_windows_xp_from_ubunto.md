---
title: "installing windows xp from ubunto"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by xqatanx on 2007-11-19
Hello there!
Neoooobee here!
This website is a god gift to us newbees.. so thanks to you all.
-----------------------------
Here is my situation:
- I had windows XP
- installed ubuntu gusty from live CD
- something happened and being a total newbee i managed to install it over my entire hard drive
- not much damage since i have no important data there.

Now, 
- I have Ubuntu running, smoothly i might add.
- But I need to install my windows again
- my NTFS settings are gone (i suppose) since the Windows installation CD at boot, gives ''missing operating system'' message
- I tried Gpart from Ubuntu to create a partition to install windows on my HDD

1- It says i have to unmount the drive. but i am on that drive.. so i cant unmount i guess unless i am outside
2- How to partition the HDD to be able to install windows and maybe have a dual boot setting?
3- are there ways on Gpart to specify the partition format (NTFS, ext3..etc)


Sorry so asking too many questions.. and thanks in advance

---

### Post by Duck2006 on 2007-11-19
You can run gparted from the live ubuntu cd or from the live cd gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

and partition it from there.

---

### Post by xqatanx on 2007-11-19
Gparted is working fine...

- but how can I use it to install windows?
- there are unmount issues?
- if i succeeded in partitioning it, how do i go from there to installing windows from the CD?
- would it boot normally?

---

### Post by Duck2006 on 2007-11-19
This may help.

[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

---

### Post by xqatanx on 2007-11-19
Thanx Duck,

I will try it. 
Although.. it assumes that Windows CD will work when booted.. but I have a problem where it does not it just give ''opertaing system missing''.

Could it be the CD problem??
or is it because the HDD is not NTFS anymore?

---

### Post by wickstopher on 2007-11-19
Do you have an actual XP disc with a full version of the operating system?  It sounds to me like you may be using some sort of recovery disk, in which case you're out of luck, because it's not going to be able to install the operating system for you.  It is an unfortunate truth that these days most manufacturers don't ship new computers with full backup versions of the operating system.  It doesn't make any sense to me, but I ran into this problem recently with a friends' newer HP computer.

---

### Post by ukripper on 2007-11-19
This could help - here is my tutorial [http://ubuntuforums.org/showthread.php?t=466234](http://ubuntuforums.org/showthread.php?t=466234)

---

### Post by xqatanx on 2007-11-19
Wickstopher:
I have the insatllation CD not the recovery. I have a custum built PC. so no recovery CDs.

---

### Post by forestpixie on 2007-11-19
I believe that the new version of gparted, you've got the link for it above- which I assume is the one you have - allows you to add to the beginning of the hdd

try resizing your existing partition and adding a new ntfs partitiona t the front of the drive- I would expect xp to find the partition then 

bear in mind that once you've installed xp it will overwwrite your grub menu and you'll have to sort that before you can get into gutsy again

---

