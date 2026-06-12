---
title: "trouble installing"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by pri123 on 2007-03-08
hello im new here and i was wondering if i could get some help :D so i downloaded ubuntu and i partitioned my hhd i get passed all of tht but when you have to mount all those things such as "root" and /boot i always get stuck it always says i dnt have a / (root) extention or sumthing along those lines. any help would be much appreciated. :)

---

### Post by wax4213 on 2007-03-08
Make sure that after you set up your partitions, you select one to mount to / and another as a linux swap.  The / is your root, and swap is the swap.  Root is usually an ext3 partition.  Some users choose to mount another partition to /home, which makes reinstalling less painful because you won't lose data that's in your home folder, but I'd suggest just using / and a swap, unless you're dualbooting.

---

### Post by Kateikyoushi on 2007-03-08
Are you trying to install ubuntu after windows to get a dual booting system ? Then read this guide. [LINK]("http://www.psychocats.net/ubuntu/installing")
If not you can let the installer do it automatically. You do not have to change /boot just set mount point for / and swap it is enough.

---

### Post by rsambuca on 2007-03-08
There is a bug in the installer program when using pre-existing partitions.  You can get around it by following these directions:  [[COLOR="Red"]Instructions[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29")

---

