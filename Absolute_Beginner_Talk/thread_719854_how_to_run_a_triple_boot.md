---
title: "how to run a triple boot"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by hershe33 on 2008-03-09
hello i  have a windows ubuntu dual boot running and I want to run kubuntu to I need some help with partitioning the  drive.

---

### Post by handydan918 on 2008-03-09
Do you have space available (unused) for new partitions? If not, gparted is your first stop, after backing it all up. Partitioning is inherently dangerous to your data. If the incantations go slightly awry, your family photos and financial records  could get turned into frogs, so back 'em up first.
Not sure how gracefully the kubuntu installer will handle the existing installations. If you use the alternate installation .iso, I believe you get the option of installing grub to root, instead of to the mbr, which can be useful.

---

### Post by ajgreeny on 2008-03-09
Why not just add kubuntu-desktop to your ubuntu installation and then chose which desktop to open at login time.  I always used to do that but have now decided that gnome is for me, however, I can assure you that the two desktops work without any major problems on a single install, other than a muddled menu system, which you can easily edit to remove unwanted menu items.

Nevertheless if you really want a triple boot, go for it.  In fact I've got Ubuntu 7.10, Mint 4, and Windows XP (hardly ever booted these days), which all work well, but in my case on two disks, so there is no problem of too many partitions on a single disk.  If you only have one drive you may need to put some or all your new partitions on an extended partition, but it would help to see your current partition table to know what to suggest.  Show us here the output of ```
sudo fdisk -l
```and we can give you a few clues as to what might be best for your system.

---

