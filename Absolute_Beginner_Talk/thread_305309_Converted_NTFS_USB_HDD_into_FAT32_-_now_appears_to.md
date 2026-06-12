---
title: "Converted NTFS USB HDD into FAT32 - now appears to have 2 partitions?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-23
Hello,

I have a 250 GB usb hard disk that I converted to FAT32 using Gparted in Dapper on my laptop (Previously this hdd was in NTFS format).

Now when I plug the usb hard disk into my laptop it appears to show up twice as if there were two partitions or two hard disks. I have attached a screenshot at the end of this post.

Here are some more details that might help you to help me :)

Info from 'fdisk -l': ( I have highlighted the relevant usb hdd in red)

```
me@ubuntunb:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3854    30957223+   7  HPFS/NTFS
/dev/hda2            3855        7152    26491185   83  Linux
/dev/hda3            7153        7296     1156680    5  Extended
/dev/hda5            7153        7296     1156648+  82  Linux swap / Solaris

[COLOR="Red"]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    b  W95 FAT32[/COLOR]
```

Info from 'mount': (I have highlighted what I think to be relevant in red)

```
me@ubuntunb:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
[COLOR="Red"]/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sda on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)[/COLOR]
```

I am a complete newbie so I do not understand how to read the data from 'mount'. I did read the forum, but I still don't understand whether in my case as shown here I have:

[LIST]
[*]2 mount points for the same partition (or drive?) or
[*]2 partitions on the drive or
[*]whether I did not partition this drive properly??[/LIST]

Additional info that might help you identify the issue:

If I copy a file to usbdisk, it does **not** show up in usbdisk-1.

What do I want to do?:

I would like to partition this 250GB usb hard disk into FAT32 and have it show up once only. I would like to have only one partition on this drive :)

Thank you in advance!

---

### Post by rlozano on 2006-11-23
hmmmmm..... im not quite sure if FAT32 is supporting 250GB is just one partition. NTFS for sure will... did you try that beofre in windows having your 250GB in a sigle partition using FAT32?

your fdisk shows only 1 sda device.

what do u have with df -h?

---

### Post by pandu.rs on 2006-11-23
AFAIK. with fat32 the maximum size of a partition is 32GB

---

### Post by Bachstelze on 2006-11-23
Wrong. The maximum size for a FAT32 FS is about 8 TiB. The only reason why Windows can't create FAT32 filesystems > 32 GiB is because M$ wants to force people to use NTFS.

---

### Post by PartisanEntity on 2006-11-23
df -h: *(i reformatted the drive since posting the above data, so now it is mounted on /dev/sdc (previously it was /dev/sda) but nothing else has changed)*

```
me@ubuntunb:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda2              25G  6.5G   18G  28% /
varrun               1014M   92K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  136K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  996M   2% /lib/modules/2.6.15-27-386/volatile
/dev/hda1              30G   16G   15G  51% /media/windows
[COLOR="Red"]/dev/sdc1             233G   16K  233G   1% /media/usbdisk
/dev/sdc              233G   16K  233G   1% /media/usbdisk-1[/COLOR]
```

---

### Post by PartisanEntity on 2006-11-23
if I do: 'sudo umount /dev/sdc' it unmounts usbdisk-1 but I still have two volumes showing up, see screenshot.

---

### Post by bodhi.zazen on 2006-11-23
You have only 1 partition on the device, "sdc1"

It is normal for fdisk to list you device this way. Here is the output from my ststem:> Disk /dev/sdc: 32 MB, 32768000 bytes
3 heads, 32 sectors/track, 666 cylinders
Units = cylinders of 96 * 512 = 49152 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         667       31983   83  Linux
Partition 1 has different physical/logical endings:
     phys=(1000, 2, 32) logical=(666, 1, 30)

Disk /dev/sdb: 32 MB, 32768000 bytes
3 heads, 32 sectors/track, 666 cylinders
Units = cylinders of 96 * 512 = 49152 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         667       31983+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1000, 2, 32) logical=(666, 1, 31)

You can see two devices, one "Linux" is jfs, the other if FAT. both have only 1 partition and both are listed as yours.

Your problem is the device is mounted twice.

Try ejecting both volumes, unplug the device, and then plug it back in again.....

---

### Post by PartisanEntity on 2006-11-23
I right clicked on each volume and selected 'eject', both volumes were ejected. If I right click on them again, the 'eject' option is not greyed out.

I then unplugged the device and then plugged it in again and both volumes showed up.

---

### Post by bodhi.zazen on 2006-11-23
> **PartisanEntity said:**
> I right clicked on each volume and selected 'eject', both volumes were ejected. If I right click on them again, the 'eject' option is not greyed out.

I then unplugged the device and then plugged it in again and both volumes showed up.

Others have reported similar behavior of usb devices on the forums. I have not seen a solution.

---

### Post by PartisanEntity on 2006-11-24
Well thanks for your help. This is a little annoying so I have decided to persue a different approach.

Since I downloaded the ext3 enabler for win xp (not sure what it is called) I will create a large ext3 partition and a small FAT32.

That way both OS's will be able to acess the drive and hopefully I wont get this annoying 2-volume strangeness, ill post back.

---

### Post by PartisanEntity on 2006-11-24
I have now created a large ext3 partition and a smaller fat32 partition.

/dev/sdc1 is ext3
/dev/sdc2 is fat32

How would I mount them in fstab t o have full permissions?

I would like the **ext3** partition to mount as **/media/bigext**

and the **fat32** to mount as **/media/smallfat**

---

### Post by bodhi.zazen on 2006-11-24
> **PartisanEntity said:**
> I have now created a large ext3 partition and a smaller fat32 partition.

/dev/sdc1 is ext3
/dev/sdc2 is fat32

How would I mount them in fstab t o have full permissions?

I would like the **ext3** partition to mount as **/media/bigext**

and the **fat32** to mount as **/media/smallfat**

Do they not auto mount ?

The fat is the same as before, use the umask option (umask=000)
```
pmount /dev/sdc2 smallfat -o umask=000
```

The ext3 is different:
```
pmount /dev/sdc1 bigext
sudo chmod 777 /media/bigext
```

You only need to chmod the first time you mount the ext3 partition.

I would advise you give each partition a label and add an entry in [fstab](http://www.ubuntuforums.org/showthread.php?t=283131)

Or use an alias in ~/.bashrc.

---

### Post by PartisanEntity on 2006-11-24
Thanks, they do mount, but what I meant was that I want to add them to fstab and I don't know what to add after:

(example) /dev/sdc1 /media/bigext (then what...?)

---

### Post by bodhi.zazen on 2006-11-24
> **PartisanEntity said:**
> Thanks, they do mount, but what I meant was that I want to add them to fstab and I don't know what to add after:

(example) /dev/sdc1 /media/bigext (then what...?)

> /dev/sdc1 /media/bigext auto users 0 0
/dev/sdc2 /media/smallfat auto users,umask=000 0 0

See my link on fstab for a more detailed explanation.

---

### Post by PartisanEntity on 2006-11-24
Ah thanks, I didnt notice the link.

---

### Post by bodhi.zazen on 2006-11-24
Working ?

---

### Post by PartisanEntity on 2006-11-24
Yes, perfectly, thank you very much.

---

### Post by bodhi.zazen on 2006-11-24
> **PartisanEntity said:**
> Yes, perfectly, thank you very much.

You have become quite an expert on Linux in the last few days 8)

---

### Post by PartisanEntity on 2006-11-24
Thanks, it would be nice if that were true :) But I really am enjoying my first serious experience with Linux generally and Dapper specifically.

It has become my main OS within a period of 2-3 weeks.

---

