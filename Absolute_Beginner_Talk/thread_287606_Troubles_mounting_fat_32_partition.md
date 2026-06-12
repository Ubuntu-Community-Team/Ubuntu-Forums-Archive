---
title: "Troubles mounting fat 32 partition"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by jdlite on 2006-10-29
I am having issue's mount my fat32 partition in ubuntu. This is what I have tried

sudo mkdir /home/jaydee/phat
sudo mount -t vfat /dev/sda5 /home/jaydee/phat -o iocharset=utf8,umask=000

This did not work so I did

dmesg

FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hdc2

This is what the output of fdisk -l is

/dev/hdc1     1         1275      10241406    83     Linux
/dec/hdc2     1276      3649      19069155    b      W95 FAT32


Please help out a fellow newb

jaydee

---

### Post by taurus on 2006-10-29
Okay, open a terminal and try editing your /etc/fstab...

```
sudo cp /etc/fstab /etc/fstab.bak <-- make a backup copy just in case...
gksudo gedit /etc/fstab
```
Now, add the following line to the end of it and save it.

```
/dev/hdc2   /media/share   vfat   defaults,umask=0000   0   0
```
Then, create a mount point and mount it...

```
sudo mkdir /media/share
sudo mount -a
```
By the way, your VFAT is on /dev/hdc2, not /dev/sda5.  You can also read this if you wish...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jdlite on 2006-10-29
Thanks for the help taurus but I seemed to figure it out. I needed to format that partition and that is why it would not mount properly. Once I did that everything was good!

jdlite

---

