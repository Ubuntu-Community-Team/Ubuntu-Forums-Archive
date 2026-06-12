---
title: "Sharing between Ubuntu and Windows on one PC"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by InuyashaDuelist on 2006-06-29
Well, before I went into Ubuntu, I used Xandros Desktop 3.02. It automatically mounted my Windows NTFS partition. However, after finding some problems and realizing how unstable it was, I decided to switch to Ubuntu (considering I had recently ordered 5 CDs), and I expected Ubuntu was going to do what Xandros did and automatically mount my NTFS partition.

However, when I attempted to access the NTFS partition, it gave a message along the lines of "Could not mount <...>". So, I went into QTParted and created a 50GB FAT32 partition to be my sharing partition. 

However, the same problem occured when I attempted to access it. Now then, I know almost nothing about Linux and was hoping to make a fresh start with something stable, in this case, Ubuntu. Besides knowing almost nothing about Linux, I know almost nothing about partitions and other such things. Here's my current partition layout.

Hard Drive 1 (320GB)
--
Windows NTFS (248GB)
Windows/Ubuntu Shared FAT32 (50GB)

Hard Drive 2 (80GB)
--
The auto-installer within Ubuntu's Live CD let Ubuntu take up the entire 80GB.


Any help would be very appreciated, I'd hate having to leave such a worthy and stable Operating System before I even got a chance to use it.:)

If any screenshots are wanted, I could gladly give them.

---

### Post by uzi09 on 2006-06-29
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

please also see sections below it for automatically doing it everytime the computer starts.

---

