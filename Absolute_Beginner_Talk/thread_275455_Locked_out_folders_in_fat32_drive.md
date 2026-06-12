---
title: "Locked out folders in fat32 drive"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by My Name on 2006-10-11
Hi guys, another noob here,

I have just started using ubuntu and I'm loving it.  Ihave a double boot sytem, with xp and ubuntu.  I have a data drive which contains all my data and windows my documents folder.  The problem i'm having is that the music folder and the my documents folders are locked ou (little padlock, non writable).  I have had a look at the permisions for the folders and the root is has only read permision aswell as all other useres.

I need to get all my folders on this drive writable for all users.

Sorry, this has probably been asked a million times i'm sure but i couldn't find any definitive answers to my problem.

I do try to solve problems myself but i need this one sorting prety quick coz the wife is dubious about using linux and i need to prove her wrong:mrgreen: 

Thanks

---

### Post by PriceChild on 2006-10-11
Could you post your /etc/fstab please... looks like an incorrect entry.

---

### Post by My Name on 2006-10-11
> **PriceChild said:**
> Could you post your /etc/fstab please... looks like an incorrect entry.

Will do so when i get home.  Thanks for the quick reply BTW

---

### Post by Tamil on 2006-10-11
See [Mounting Windows Partitions in Ubuntu](http://www.psychocats.net/ubuntu/mountwindows.php)

---

### Post by My Name on 2006-10-11
> **PriceChild said:**
> Could you post your /etc/fstab please... looks like an incorrect entry.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

