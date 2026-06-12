---
title: "Mount NTFS Drive // Format NTFS Drive"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by AdrenalineJunkie on 2007-03-06
Hello World.

_My Problem_

I have a Hard Drive Connected in my computer, as you do, and it was formatted to NTFS with my install of windows, back before i chose ubuntu instead. I want to be able to use it, but i dont know how to mount an NTFS drive, since the instructions i have found confuse me a bit.

Although, is there a way for me to format the drive to a format that will allow me to use it normally from in ubuntu, this would be a more convenient option.

Sorry if this seems like a **really** stupid question.

But thanks for any help in advance.

**AdrenalineJunkie**

---

### Post by taurus on 2007-03-06
Do you want to format it to ext3 (default filesystem for Ubuntu)?  What are the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by puelly on 2007-03-06
Hey there,

This link should get you started on the right track.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Regards

---

### Post by AdrenalineJunkie on 2007-03-12
**Yes i would like to format it to ext3.**

```
sudo fdisk -l
```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9589    77023611   83  Linux
/dev/sda2            9590        9729     1124550    5  Extended
/dev/sda5            9590        9729     1124518+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4984    40033948+   7  HPFS/NTFS
/dev/hdb2            4985        4998      112455    f  W95 Ext'd (LBA)


```
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G   62G  7.4G  90% /
varrun                189M   92K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
procbususb             10M  168K  9.9M   2% /proc/bus/usb
udev                   10M  168K  9.9M   2% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   18M  172M  10% /lib/modules/2.6.17-11-generic/volatile


Apologies For the Late Reply.

---

### Post by taurus on 2007-03-12
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```
And if you want to mount the other partition, you need to use gparted from Ubuntu to create a logical partition, /dev/hdb5, since /dev/hdb2 is an extended partition right now.

---

### Post by gh0st on 2007-03-12
This might be an overkill for your situation but why don't you use the Gparted Live CD? It will allow you to boot up and sort out your partitions any way you want with a nice easy GUI. I like it anyway :) 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Download the Live CD, burn it, boot it. Hope that helps in some way.

Good luck :)

---

### Post by AdrenalineJunkie on 2007-03-12
Thanks a lot people.

Another Reason why i love ubuntu; the community support :)

---

