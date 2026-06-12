---
title: "How do perform backups on a dual boot system?"
date: 2009-11-24
forum: Apple Hardware Users
---

### Post by JohnAtilano on 2009-11-24
I've been fooling around with Ubuntu on a virtual machine and I've decided I'd like to install it on my Macbook Pro 5,1.  This will be a dual-boot system (OS X & Ubuntu).

Currently I use SuperDuper! to clone my hard drive to an external firewire drive.  After I have Ubuntu installed, how are back ups handled?  

1.  After installing Ubuntu, when I clone my drive with SuperDuper! will the Ubuntu system also be copied?

2.  After running a dual-boot system for some months, If for some reason I decide I no longer want Ubuntu on my system can I delete the Ubuntu partition and then use a recent SuperDuper! backup to restore my OS X system?

I don't know enough about boot partitions, EFI, and Master boot records to know if SuperDuper! will be copying this information and hence create an unusable OS X system.

Any information, links, etc. the community can provide would be greatly appreciated.

---

### Post by linuxopjemac on 2009-11-24
If you want to clone a complete hard drive, including partition scheme etcetera, I suggest CloneZilla. For simple backups, I use the open source program Luckybackup, very versatile. I also incrementally backup my OSX partition with this tool.

---

### Post by dennis123123 on 2009-11-24
Use dd and netcat, can't get any simpler or more standardised:


If you have a server/backup PC/etc:

Server:
# nc -l -p 3333 | dd of=/home/user/backups/macbookbackup.dd.gz

Macbook (linux/livecd/etc):
# dd if=/dev/sda | gzip -9 | nc *<server's-ip>* 3333




If you have a USB HDD etc:
Macbook:
# dd if=/dev/sda | gzip -9 | dd of=/mnt/usbhdd/macbookbackup.dd.gz






You can take out the gzip, but it will use up much more disk space as it is a perfect bit-for-bit clone so will be the full size of the drive.

---

