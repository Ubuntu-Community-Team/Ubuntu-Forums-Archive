---
title: "Partion Help"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Link360 on 2007-02-25
Ive installed Ubuntu 6.06 on my computer with Windows XP. The partion gave Ubuntu a lot 

more storage than Windows XP. Now im not able to install any new games for my computer 

because of lack of hard drive space in Windows XP. Will someone tell me how to give Windows 

XP more hard drive space without having to reinstall Ubuntu. Thanks in advance.

---

### Post by raja on 2007-02-25
You can use the Ubuntu live cd or Gparted live cd to shrink the linux partition. Create a new NTFS or FAT partition in the free space created and you will be able to use it from windows.

---

### Post by Link360 on 2007-02-25
will you tell me how to do that?

---

### Post by Link360 on 2007-02-25
bump

---

### Post by raja on 2007-02-26
gparted is a graphical partition editor. You can use it from the ubuntu live cd or you can download and burn the gparted live cd for this. Boot with that cd and run gparted to see your partitions. Identify your ubuntu partition and just shrink it (you can type in the new size or shrink it with the mouse). Once that is done you have free space after that partition. Click in this free space and create a new partition. Format this as FAT or NTFS and you will then be able to use it from windows. It seems a little difficult when explained like this, but is easier when you do it. And till you commit, no changes are done - you can always undo something if you are not sure.

---

### Post by gameman12 on 2007-02-26
raja's right just be careful when you do this

i shrunk my partions and i'm now stuck with all sorts of grub errors.

BACK UP ANYTHING IMPORTANT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

