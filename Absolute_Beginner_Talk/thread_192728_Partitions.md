---
title: "Partitions"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-09
I would like to make a dual-boot with windows and ubuntu, right now I have only ubuntu.

right now when I tryied to instal windows it sayd that windows cant recognize this partition type or something.

so heres what I need (I think):

I need to make current partition smaller - so there will be un-formated space on HD and then simply format it to NTFS..

But I dont know how to make my current partition smaller :???: 

__________________

if I cant make it like that then how can I make dual-boot without loosing data?

---

### Post by J-Gaming on 2006-06-09
when I installed ubuntu, I saw (on live-cd maybe) some things that changed partitions (also apears on installind ubuntu) but after installing KDE (I use gnome) aswell it seems to be disapeared and whole menu is actually messed up..

---

### Post by J-Gaming on 2006-06-09
Ok, I found out that somewhy GParted was uninstalled..

but when I right click on parted space then I cant choose option "resize" I cant select anything except "unmount" and "information"

---

### Post by catlett on 2006-06-09
You can't make changes to a mounted partition, you have to unmount the partition before you do anything else. Choose unmount and comtinue.
You might want to try gparted live, it runs off of a live cd, which means the drive never gets mounted and you can make changes right there and then.[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

