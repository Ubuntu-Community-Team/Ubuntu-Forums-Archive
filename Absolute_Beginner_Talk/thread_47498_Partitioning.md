---
title: "Partitioning"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by porkfilledbutcher on 2005-07-08
:-x [FONT=Times New Roman][SIZE=3]*How do I partition my hard drive? After selecting "Manually Edit Partition", I can't seem to adjust the size.*[/SIZE][/FONT]

---

### Post by ubuntu_demon on 2005-07-08
[QUOTE=porkfilledbutcher]:-x [FONT=Times New Roman][SIZE=3]*How do I partition my hard drive? After selecting "Manually Edit Partition", I can't seem to adjust the size.*[/SIZE][/FONT][/QUOTE]


The best solution is asking someone to do it for you if you are afraid that you might mess up. But if you decide to do this  first backup your important data. (in case you make a mistake somewhere and lose it all)

If you want to resize your XP partition. The easiest solution is using partion magic in windows. You can also download this cd-rom [http://www.sysresccd.org](http://www.sysresccd.org) and boot the live-cd. use gparted( the most user friendly partitioning application in linux).

Whichever of those two you do .. you gotta do this : resize your windows partition and create free space. (I recommend at least 6 gb)

Ater you have created this free space just boot from the ubuntu installer cd. Create your partitions in this free space. (the next release breezy will be able to automatically partition the free space during install if you want it to)

you should do something like this :
-create 4-5 gb  / ext3 partition
-create 1-2 gb swap
-create a fat32 partition to share your files with windows (on fat32 both linux and windows can read and write) ....0-10 gb
-use the rest for your free space for your home partion

maybe you should also take a look in this thread (since there's also a link to a guide) : [http://www.ubuntuforums.org/showthread.php?t=47475](http://www.ubuntuforums.org/showthread.php?t=47475)

After the installation be sure to check out : [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by az on 2005-07-08
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

