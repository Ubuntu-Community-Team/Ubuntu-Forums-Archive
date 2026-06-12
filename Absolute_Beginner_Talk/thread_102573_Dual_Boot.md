---
title: "Dual Boot"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by albert313 on 2005-12-12
I loaded Ubuntu without a hitch but I am dual booting with Win XP. Can I eliminate the dual boot. Also WinXp Explore does not see the second drive where I installed Ubuntu and I can't find something similar in Ubuntu to show the drive and DIRs.

---

### Post by hesee on 2005-12-12
[QUOTE=albert313]I loaded Ubuntu without a hitch but I am dual booting with Win XP. Can I eliminate the dual boot. Also WinXp Explore does not see the second drive where I installed Ubuntu and I can't find something similar in Ubuntu to show the drive and DIRs.[/QUOTE]

Hi,
Do you want to remove windows completely or remove it from bootlist? If it's just boot list that's annoying you, a simple and secure way would be to hide the list, like this:

[http://makuchaku.info/amnesty/#hidegrub](http://makuchaku.info/amnesty/#hidegrub)

From windows, you don't see linux partitions(drives), because they are not ntfs/fat partitions. From ubuntu however, you should be able to see your windows drives (although they are not named C,D... etc) Take a look at the Places -> Removable Media for example(Assuming you are using breezy), and you should see mounted partitions. Or open nautilus(file browser) and open directory /media/.

---

### Post by tay on 2005-12-12
this should help you mount your windows partition

mount -l (list mounted)
umount  (type,  usbfs, hda1, etc.. ) (unmount)
cd /mnt  (go to mounted folder)
ls -a  (show all folders in /mnt or any dir)
mount -t (type) fat32 (or ntfs) hda5 /mnt

i use this alot to mount hard drive from a live cd to fix problems:
mount -t ext3 /dev/hda2 /mnt
cd /mnt
ls -a
cd ./ (hda that i want to edit)

---

### Post by ShiftyPowers on 2005-12-20
[QUOTE=hesee]Hi,
Do you want to remove windows completely or remove it from bootlist? If it's just boot list that's annoying you, a simple and secure way would be to hide the list, like this:

[http://makuchaku.info/amnesty/#hidegrub](http://makuchaku.info/amnesty/#hidegrub)

From windows, you don't see linux partitions(drives), because they are not ntfs/fat partitions. From ubuntu however, you should be able to see your windows drives (although they are not named C,D... etc) Take a look at the Places -> Removable Media for example(Assuming you are using breezy), and you should see mounted partitions. Or open nautilus(file browser) and open directory /media/.[/QUOTE]

Heese, how can I actually remove all of windows in this scenario?

---

