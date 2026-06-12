---
title: "convert NTFS to LINUX"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by El Viejo Lobo on 2007-02-14
How to format the NTFS to be a linux hard drive

yigal@ubuntux2:~$ sudo fdisk  -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4810    38636293+  83  Linux
/dev/hda2            4811        4998     1510110    5  Extended
/dev/hda5            4811        4998     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4772    38331058+   7  HPFS/NTFS
/dev/hdc2            4773        4865      747022+   f  W95 Ext'd (LBA)
/dev/hdc5            4773        4865      746991   82  Linux swap / Solaris
yigal@ubuntux2:~$

---

### Post by Dylnuge on 2007-02-14
Not quite sure what you mean.

If you want to make it into an Ext3 Hard Drive (Ext3 is the best option for a Linux Hard Drive), you need to format it. It will be quite simple, but you will lose all of your data.

If you want to make it compatible with Linux, so it can be read by Linux, but keep it on Windows, you can leave it as an NTFS. Ubuntu can read and copy data from an NTFS, it just cannot write to it.

If you are still actively using Windows and believe you will be sharing files in both directions (you will be needing Linux files on Windows), it needs to be a FAT hard drive, probably FAT32. This will also require a loss of all data.

Which option do you need?

---

### Post by taurus on 2007-02-14
Do you want to format /dev/hdc1 to ext3?  Make sure /dev/hdc1 is not mounted first and do

```
sudo mke2fs -j /dev/hdc1
```

Then add this line to /etc/fstab so it would be mounted each time you turn on your machine.

```
/dev/hdc1   /media/hdc1   ext3   defaults   0   1
```
And of course, create the new mount point for it before you mount it.

```
sudo mkdir /media/hdc1
sudo mount -a
df -h
```

---

### Post by igknighted on 2007-02-14
To format the drive you will want a program called gparted.  It may be installed, or you can install it from the repo's.  You could also use the live CD to do it (probably easiest).

I do have an unrelated question.  You have two HDs, each on a seperate IDE cable.  Is there a reason for this?  If you have an optical drive (cd/dvd) installed, it would be sharing a cable with one of theose HDs, and cutting the speed of data transfer to that hard drive by a factor of 3.  You could drastically improve HD performance by putting both HDs on the same cable, and all you optical drives on another.

---

### Post by El Viejo Lobo on 2007-02-14
I tried to do what Taurus recommended and this is what I got when I go to "places"

/media/hdc1/lost+found

I think I am half way to get the Hd working in Ubuntu. What I am missing?



yigal@ubuntux2:~$ gksudo gedit /etc/fstab
 
(gedit:5204): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
yigal@ubuntux2:~$ sudo mkdir /media/hdc1
yigal@ubuntux2:~$ sudo mount -a
mount: special device /dev/hdd1 does not exist
yigal@ubuntux2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G   29G  5.6G  84% /
varrun                252M  120K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  168K  9.9M   2% /proc/bus/usb
udev                   10M  168K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-11-generic/volatile
/dev/hdc1              36G  177M   34G   1% /media/hdc1
yigal@ubuntux2:~$ 

As for igknighted question about the IDE and the two HDs. When I connect the 2 HDs to the same IDE I can not boot the PC.  I do not have any Windows (at 100 meter from home) The Hd NTFS used to be the windows store HD and it is suppose to be Ubuntui's store HD. the data it have is saved in dvd.
yigal@ubuntux2:~$ $ sudo fdisk -l
bash: $: command not found
yigal@ubuntux2:~$  sudo fdisk -l         THIS IS THE LAST FDISK
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4810    38636293+  83  Linux
/dev/hda2            4811        4998     1510110    5  Extended
/dev/hda5            4811        4998     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4772    38331058+   7  HPFS/NTFS
/dev/hdc2            4773        4865      747022+   f  W95 Ext'd (LBA)
/dev/hdc5            4773        4865      746991   82  Linux swap / Solaris
yigal@ubuntux2:~$ 

Thanks

---

### Post by taurus on 2007-02-14
The lost+found directory in /media/hdc1 is normal because ext3 needs it.  Now, you may want to change the ownership of /media/hdc1 so you can write to it without using the sudo.

```
sudo chown -R **yigal**:**yigal** /media/hdc1
```
(I assume your login name is **yigal**...)

p.s.  Did you have an extra entry in /etc/fstab for /dev/hdd1?  Post /etc/fstab here if you're not sure.

```
cat /etc/fstab
```

---

### Post by El Viejo Lobo on 2007-02-14
I can use hdc1 to read and write but can not rename or mope to trash directories.
is it have to be with no rename and trash or it can be fixed?
Thanks.:guitar:

---

### Post by taurus on 2007-02-15
What do you mean by trash directories?  Not sure if I understand what you meant.

---

### Post by El Viejo Lobo on 2007-02-15
I do not know way but at the firsts steps in the ext3 disk the right click menu show the options of rename and trash - inactive.
It is perfect now.
A lot of thanks.:guitar:

---

### Post by highneko on 2007-02-15
> **taurus said:**
> ```
sudo chown -R **yigal**:**yigal** /media/hdc1
```
(I assume your login name is **yigal**...)


A little trick for this could maybe be:
if [ $USER != "root" ]; then sudo chown $USER:$USER /directory; fi

---

