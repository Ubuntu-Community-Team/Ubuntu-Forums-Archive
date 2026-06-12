---
title: "How to partition my second hard"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by milad on 2007-04-21
I've decided to install my old hard drive in my PC. But first, I want to delete all of it's partitions and create new ones. So which file system should I choose? Ext3 ? or maybe FAT32?

---

### Post by mikewhatever on 2007-04-21
What are you planing to use that drive for? Do you have Windows installed and what it to access the drive?

---

### Post by milad on 2007-04-21
I want to use it for saving pictures and movies and ..
I don't have windows installed yet but I prefer this hard drive to be compatible with Windows.

---

### Post by GSF1200S on 2007-04-21
> **milad said:**
> I want to use it for saving pictures and movies and ..
I don't have windows installed yet but I prefer this hard drive to be compatible with Windows.

If you want it to be for both, I would use gparted to format the drive in NTFS format, and then use NTFS3g to mount the partition under Ubuntu.

Ntfs3g allows read/write access of NTFS partitions. And of course, WinXP uses NTFS, so it will be able to use this drive as well.

If you are using another version of Windows, then partition it to Fat32 format, and youre done. Ubuntu and any version of windows can read/write to Fat32, but it gets fragmented much faster than NTFS, so if youve got XP, I would definitely go the NTFS/NTFS3g route.

To install gparted, open a terminal and type:

sudo aptitude install gparted

When its done, type in a terminal:

sudo gparted

---

### Post by mikewhatever on 2007-04-21
If the drive is only used for storage, FAT32 is the easiest way to go. Both Ubuntu and Windows will have full access to it, and you'll probably not notice any performance differences. EXT3 is a more efficient file system, but you'd have to deal with enabling Windows write support for it.

---

### Post by milad on 2007-04-21
Tx a lot. I've have installed gparted and deleted all of my old partitions. but when i wanna create new one, the NTFS option is disbaled. i think GParted can't create NTFS partitions. do u know any other software?

---

### Post by GSF1200S on 2007-04-21
> **milad said:**
> Tx a lot. I've have installed gparted and deleted all of my old partitions. but when i wanna create new one, the NTFS option is disbaled. i think GParted can't create NTFS partitions. do u know any other software?

Well hey.. mikewhatever has some good advice. Fat32 will give performance decrease when its what the OS is on, but when its just a storage device, you wont have issues. Im pretty sure you can defragment it if you ever needed to.

So, I would say go ahead and partition it to Fat32- both windows and Linux will be able to read/write to it.

---

### Post by GSF1200S on 2007-04-21
[http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

This seems to be a tool that will allow writing/resizing of NTFS according to this forum thread:

[http://www.fedoraforum.org/forum/archive/index.php/t-1105.html](http://www.fedoraforum.org/forum/archive/index.php/t-1105.html)

Good Luck!

---

