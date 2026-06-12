---
title: "USB harddisk mounted as CDROM"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by th00ht on 2008-04-21
I have an external USB harddisk that Ubuntu 7.10 attempts to mount as CDROM. How can I tell Ubuntu to auto mount this harddisk as harddisk.
(btw sudo mount -t vfat /dev/sda1 /media/TREKSTOR works fine)

Here is some details:
```
j@pan:~$ sudo fdisk -l

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c13dd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14240   114382768+  83  Linux
/dev/hdc2           14241       14593     2835472+   5  Extended
/dev/hdc5           14241       14593     2835441   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6271337b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    c  W95 FAT32 (LBA)
j@pan:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=c0561e79-57bb-4e1c-aa8c-cebd8f351f6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=0cfca185-56ce-485d-a5c0-6b9b0549341c none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
j@pan:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1             108G   49G   54G  48% /
varrun                474M  216K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   80K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   34M  440M   8% /lib/modules/2.6.22-14-generic/volatile
j@pan:~$ 


```

---

### Post by wesleybailey on 2008-04-22
This is what my fstab looks like.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dd1a645b-7c08-47e9-bcc8-27c6f7eeac7a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=C840-AA00  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=2BC5-73B2  /shared         vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=3f4944e2-3ac3-4cc1-a438-231b711223b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



I would just comment out that cdrom line, and try this

> 
#/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


/dev/sda1       /media/TREKSTOR vfat defaults,utf8,umask=007,gid=46 0       1


Naturally you will have to umount the disk detected as cdrom first and then mount -a

---

### Post by th00ht on 2008-04-22
> **wesleybailey said:**
> 
I would just comment out that cdrom line, and try this


Thanks wesley, I did comment out the cdrom line. But now I can only mount the harddisk manually, not cool. How can I tweak Ubuntu's magic to mount the HD automagically?

---

### Post by DBrocks on 2008-04-22
You could write a script that does it.

```
sudo mount -t vfat /dev/sda1 /media/TREKSTOR
```

chmod 0777 path/to/your/script.sh

---

### Post by DBrocks on 2008-04-22
You could write a script that does it.

```
sudo mount -t vfat /dev/sda1 /media/TREKSTOR
``````
chmod 0777 path/to/your/script.sh

```

---

### Post by th00ht on 2008-04-22
Thanks. 
And but what should I do to have Ubuntu mount the harddisk automatically?

---

### Post by th00ht on 2008-04-22
btw it now complains again when I plug in the device 

Cannot mount volume.

details:
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)


I did not specific a mount_point Ubuntu did. Where can I change the mount_point that ubuntu uses?

---

### Post by wesleybailey on 2008-04-22
This command will take you to a GUI, that has all the setting for auto mounting.

```

gconf-editor /system/storage/default_options 

```

---

### Post by th00ht on 2008-04-22
I cannot see anything wrong at the vfat setting in storage / default_options in gconf-editor. My harddisk is not listed there.



Btw. The Cannot mount volume dialog is quite useless as it does not offer a reason why it cannot mount neither a way of changing the way it mounts. dmesg does not log any errors

---

### Post by th00ht on 2008-04-23
Steps to resolve this issue.

1) At first ignore the error messages from ubuntu

2) Find the location of the drive using fdisk -l

3) Attach the drive with 

sudo mount /dev/sdx1 /mnt 

(replace the x with the actual letter from step 2)

4) The drive should appear on the desktop, if not reboot your Ubuntu and try again. 

5) Right click on the drive and select properties

6) There is two tabs at the right hand side Drive and Volume. It is guessing what the developers meant with either of them but select Settings on each of them and make sure there is nothing in the Mount point, File System, and Mount options.

7) Close the properties and detach the disk with

sudo umount /mnt 

8) Now unplug the external harddisk and plug it in again. 

It now should be recongnized.

A note to the ubuntu developers: please remove the Permissions tab as changes in this screen are ignored silently. The Emblems tabs seems to be pretty useless as well.

---

