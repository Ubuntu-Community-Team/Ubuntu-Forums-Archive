---
title: "Please help me I'm as new as it gets to this."
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by clbrooksva on 2006-03-09
I just need to know how i can reformat my hd to a complete fat 32 file sys using Gparted. I am doing this to reinstall windows(dont have me) as I have not been able to have any success using wine or installing it. I just simply have too much software to sacrifice for this os. Thanks.

---

### Post by prizrak on 2006-03-09
Why do you want it to run on FAT32? I'm not sure how you do it with Gparted, I'm not sure it formats partitions at all. You might wanna try going through the Ubuntu install, when you get to partitioning just go into manual mode nuke your partitions and create one big one with FAT32 (I think fdisk gives you that as one of the choices). Another alternative is create a smallish system partition that runs NTFS where Windows itself and the software will be installed. Then create another partition with FAT32 Windows itself will let you format it that way with it's disk manager.

---

### Post by earobinson on 2006-03-09
Windows should be able to format the drive for you during the install.

---

### Post by az on 2006-03-09
[QUOTE=clbrooksva]I just need to know how i can reformat my hd to a complete fat 32 file sys using Gparted. I am doing this to reinstall windows(dont have me) as I have not been able to have any success using wine or installing it. I just simply have too much software to sacrifice for this os. Thanks.[/QUOTE]
The windows installer should be able to delete the partitions for you.  It will then ask you to create a new NTFS or fat partition.

If it cannot delete them because it thinks the partition table is meesed up, you can use fdisk to create an empty partition table and then re-run the winodws installer.

---

