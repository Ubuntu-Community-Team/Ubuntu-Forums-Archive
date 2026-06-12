---
title: "Unable to mount a partition"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Seseli on 2007-01-16
Hi, 

I run Ubuntu 6.10 on one hard drive. I have a second hard drive which is partitioned into one NTFS partition, where my Windows system is installed, and one extended partition containing a logical partition which is formatted with ext3. The NTFS partition mounts just fine, but I can't get the ext3 partition to mount. I have tried typing 

sudo mount /dev/hda5 /media/hda5

and it then asks for my password and a new command line appears, but nothing happens. When I open gparted it tells me that the partition is not mounted. 

I've also tried modifying /etc/fstab. Originally, the line about this partition said

# /dev/hda5   
UUID=50442CD8442CC318 /media/hda5   ntfs   defaults,nls=utf8,umask=007,gid=46   0    1

which is obviously wrong since it's not an ntfs partition. So I tried changing it to 

# /dev/hda5
UUID=50442CD8442CC318  /media/hda5  ext3    defaults    0       1

but then the file system check failed, saying it could not resolve the UUID. So I took out the line about /dev/hda5 completely, and the computer started ok, but I still can't mount the partition. I'd be grateful for some help.

---

### Post by xyz on 2007-01-16
This is a good place to go to:
[Click on "Mount Windows" - "Mount Linux"]("http://www.psychocats.net/ubuntu/index.php")
...on the right hand of your screen.

---

### Post by Seseli on 2007-01-17
Thank you for the help, it's working now!

---

