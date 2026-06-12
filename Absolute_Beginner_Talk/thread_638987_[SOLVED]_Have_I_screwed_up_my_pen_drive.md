---
title: "[SOLVED] Have I screwed up my pen drive?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-12
I was recently trying to install Gutsy on my pen drive.  Something got mixed up and now I can't get my pen drive to work.  I insert it into the USB port but it is not recognised.  Is there a way to format this, or is there some other way I can get it functioning again?

TIA

---

### Post by odiseo77 on 2007-12-12
Not knowing which device is your USB flash drive is hard to format it. Try the following (I'm not sure, but maybe this helps): insert the USB flash drive into the USB port, immediately after that, execute the following commands in two separated terminals:

```
tail -f /etc/mtab
```

```
sudo tail -f /var/log/messages
```

(monitor the outputs).

You don't need to post the complete output of the last command here; only the relevant line, where it says you plugged the USB flash drive in.

Greetings.

---

### Post by L Campbell on 2007-12-12
> **odiseo77 said:**
> Not knowing which device is your USB flash drive is hard to format it. Try the following (I'm not sure, but maybe this helps): insert the USB flash drive into the USB port, immediately after that, execute the following commands in two separated terminals:

```
tail -f /etc/mtab
```

```
sudo tail -f /var/log/messages
```

(monitor the outputs).

You don't need to post the complete output of the last command here; only the relevant line, where it says you plugged the USB flash drive in.

Greetings.

Hi, thanks for your interest here.

Hopefully this makes sense 'cause I'm in way over my head.  :-)

qwer@qwer-desktop:~$ tail -f /etc/mtab

/dev/sda1 / ext3 rw,errors=remount-ro 0 0

proc /proc proc rw,noexec,nosuid,nodev 0 0

---

### Post by odiseo77 on 2007-12-12
hmm, it's strange. I don't find your USB device there (and it should appear there). In my case, when I insert my USB device I see this:

```
/dev/sdc /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
```

The /etc/mtab entry you posted above seems to be your first HD partition (so don't mess with it while we're not sure :))

Could you insert your USB device, wait for about 1 or 2 minutes and post the complete outputs of:

```
tail -f /etc/mtab
cat /etc/fstab
sudo fdisk -l
```

Regards.

---

### Post by L Campbell on 2007-12-13
> **odiseo77 said:**
> hmm, it's strange. I don't find your USB device there (and it should appear there). In my case, when I insert my USB device I see this:

```
/dev/sdc /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
```

The /etc/mtab entry you posted above seems to be your first HD partition (so don't mess with it while we're not sure :))

Could you insert your USB device, wait for about 1 or 2 minutes and post the complete outputs of:

```
tail -f /etc/mtab
cat /etc/fstab
sudo fdisk -l
```

Regards.

Thank you for sticking with me.

qwer@qwer-desktop:~$ tail -f /etc/mtab

/dev/sda1 / ext3 rw,errors=remount-ro 0 0

proc /proc proc rw,noexec,nosuid,nodev 0 0

/sys /sys sysfs rw,noexec,nosuid,nodev 0 0

varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0

varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0

udev /dev tmpfs rw,mode=0755 0 0

devshm /dev/shm tmpfs rw 0 0

devpts /dev/pts devpts rw,gid=5,mode=620 0 0

lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0

securityfs /sys/kernel/security securityfs rw 0 0

cat /etc/fstab

sudo fdisk -l


Not good, huh?    :-)

---

### Post by Dr Small on 2007-12-13
Did you run the last two commands ?

---

### Post by L Campbell on 2007-12-13
> **Dr Small said:**
> Did you run the last two commands ?

Thank you for noticing this.

Here is the whole thing:-

qwer@qwer-desktop:~$ tail -f /etc/mtab

/dev/sda1 / ext3 rw,errors=remount-ro 0 0

proc /proc proc rw,noexec,nosuid,nodev 0 0

/sys /sys sysfs rw,noexec,nosuid,nodev 0 0

varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0

varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0

udev /dev tmpfs rw,mode=0755 0 0

devshm /dev/shm tmpfs rw 0 0

devpts /dev/pts devpts rw,gid=5,mode=620 0 0

lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0

securityfs /sys/kernel/security securityfs rw 0 0


qwer@qwer-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=ad88ec7d-a2db-4324-ba39-1b65aa41ef03 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda5

UUID=7d67798c-2298-4f5d-b210-b99cf27e7bf8 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

qwer@qwer-desktop:~$ sudo fdisk -l

[sudo] password for qwer:



Disk /dev/sda: 41.1 GB, 41110142976 bytes

255 heads, 63 sectors/track, 4998 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xf1121ebf



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        4787    38451546   83  Linux

/dev/sda2            4788        4998     1694857+   5  Extended

/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)



Disk /dev/sdb: 4244 MB, 4244636160 bytes

255 heads, 63 sectors/track, 516 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00069633



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1         486     3903763+  83  Linux

/dev/sdb2             487         516      240975    5  Extended

qwer@qwer-desktop:~$

---

### Post by odiseo77 on 2007-12-13
Do you have two hard drives installed in your machine? Also, what's the storage capacity of your USB flash drive? (just trying to figure out whether or not /dev/sdb is your USB flash drive **before** attempting to do anything with it).

EDIT: Also, could you extract your USB flash drive, wait for about 1 minute, and execute ***sudo fdisk -l*** again? (so we're completely sure which one's your USB device).

---

### Post by L Campbell on 2007-12-13
> **odiseo77 said:**
> Do you have two hard drives installed in your machine? Also, what's the storage capacity of your USB flash drive? (just trying to figure out whether or not /dev/sdb is your USB flash drive **before** attempting to do anything with it).

EDIT: Also, could you extract your USB flash drive, wait for about 1 minute, and execute ***sudo fdisk -l*** again? (so we're completely sure which one's your USB device).

I have only one HD and it is 40GB

The USB flash drive is 4GB

qwer@qwer-desktop:~$ sudo fdisk -l 
[sudo] password for qwer:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1121ebf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris
qwer@qwer-desktop:~$ 

Kind regards.

---

### Post by Dr Small on 2007-12-13
It looks like this is it:
```
Disk /dev/sdb: 4244 MB, 4244636160 bytes
255 heads, 63 sectors/track, 516 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069633

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 486 3903763+ 83 Linux
/dev/sdb2 487 516 240975 5 Extended


```

---

### Post by odiseo77 on 2007-12-13
Yep, as Dr. Small says, it seems to be /dev/sdb. So try this: insert your flash drive into the USB port, wait for about 2 minutes, then execute:

```
mkdosfs -F 16 /dev/sdb
```

(if you get a "permission denied" error, put ***sudo*** at the beginning of the command).

The command above should format your USB flash drive in FAT16 format (if you want it in FAT32, try ***mkdosfs -F 32 /dev/sdb*** instead).

Regards.

---

### Post by Dr Small on 2007-12-13
Or simpler, have you tried going into Gparted and seeing if the USB would show up in there ? If so, you could just format it right from there.

Dr Small

---

### Post by L Campbell on 2007-12-13
> **odiseo77 said:**
> Yep, as Dr. Small says, it seems to be /dev/sdb. So try this: insert your flash drive into the USB port, wait for about 2 minutes, then execute:

```
mkdosfs -F 16 /dev/sdb
```

(if you get a "permission denied" error, put ***sudo*** at the beginning of the command).

The command above should format your USB flash drive in FAT16 format (if you want it in FAT32, try ***mkdosfs -F 32 /dev/sdb*** instead).

Regards.

This is what I get:-

qwer@qwer-desktop:~$ mkdosfs -F 16 /dev/sdb
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: Will not try to make filesystem on full-disk device '/dev/sdb' (use -I if wanted)
qwer@qwer-desktop:~$ 

Does that indicate that I should do it again, prefaced by sudo?

Also, what I want to do is to load Gutsy onto the flash drive so, should I use FAT 16 or FAT32?  Or is there really any difference for my application.

Kind regards.

---

### Post by odiseo77 on 2007-12-13
Better try with Gparted, as Dr Small suggests. As for the file system type, I'm not sure, since I've never installed Ubuntu into a USB flash drive. But I think you should be able to choose which device to install Ubuntu into (and Ubuntu will probably format it in ext3 when installing).

---

### Post by L Campbell on 2007-12-13
> **odiseo77 said:**
> Better try with Gparted, as Dr Small suggests. As for the file system type, I'm not sure, since I've never installed Ubuntu into a USB flash drive. But I think you should be able to choose which device to install Ubuntu into (and Ubuntu will probably format it in ext3 when installing).


Okay.

Thank you very much for all your help.

---

### Post by L Campbell on 2007-12-13
> **Dr Small said:**
> Or simpler, have you tried going into Gparted and seeing if the USB would show up in there ? If so, you could just format it right from there.

Dr Small

Thanks for your suggestion.

I tried some searches for Gparted but only found stuff about making partitions.

How would I 'go into' Gparted, please?

---

### Post by odiseo77 on 2007-12-13
Go to 'System>Administration'. You'll find there Gparted (or 'Partition Editor' in my spanish Gnome). If it's not there, install it with:

```
sudo apt-get install gparted
```

If you are going to use Gparted, make sure the device you format is **/dev/sdb** and **NOT** /dev/sda (/dev/sda is your hard drive).

Greetings.

---

### Post by Dr Small on 2007-12-13
First, open gparted:
```
gksudo gparted
```

And then up in the top, right hand corner, should be your hard drive (/dev/sd**x**)
Click that, and it should be a drop down. If you have your flash drive plugged in, it should show up in that drop down.

Then, proceed to select it, and then you can right click on the partition, Select "Format To" and change it to whatever filesystem you please.

Dr Small

Edit, sorry odiseo77, I forgot that gparted had to be installed first :p

---

### Post by papuccino1 on 2007-12-13
I'm following this thread because I have the same problem. But gparted is stuck on scanning all drives. For the past 10 minutes!

How long does it usually take?

---

### Post by Dr Small on 2007-12-13
> **papuccino1 said:**
> I'm following this thread because I have the same problem. But gparted is stuck on scanning all drives. For the past 10 minutes!

How long does it usually take?
It generally doesn't take that long. I have had that happen to me, in the past, but I don't recall a fix for it. Maybe a reboot would help ?

---

### Post by L Campbell on 2007-12-13
> **Dr Small said:**
> First, open gparted:
```
gksudo gparted
```

And then up in the top, right hand corner, should be your hard drive (/dev/sd**x**)
Click that, and it should be a drop down. If you have your flash drive plugged in, it should show up in that drop down.

Then, proceed to select it, and then you can right click on the partition, Select "Format To" and change it to whatever filesystem you please.

Dr Small

Edit, sorry odiseo77, I forgot that gparted had to be installed first :p

OK, thanks,I feel like I'm on a roll now.   :-)

The flash drive shows up (screenshot) but I haven't been able to get it to do anything.  Right clicking, wherever I try it, hasn't brought up any options, other than 'New'.

---

### Post by L Campbell on 2007-12-13
> **L Campbell said:**
> OK, thanks,I feel like I'm on a roll now.   :-)

The flash drive shows up (screenshot) but I haven't been able to get it to do anything.  Right clicking, wherever I try it, hasn't brought up any options, other than 'New'.

Now I have found that clicking on 'New' gives me this (screenshot)

Is this what I need to do now?

---

### Post by Dr Small on 2007-12-13
Yes. Sorry for the long delay, I have been off the pc for awhile.
Since there is no partition to reformat, you will need to create a partition.

Create one, make it the fullsize of the disk, and then create it. You should have filesystem options when creating it, too.

Dr Small

---

### Post by L Campbell on 2007-12-13
> **Dr Small said:**
> Yes. Sorry for the long delay, I have been off the pc for awhile.
Since there is no partition to reformat, you will need to create a partition.

Create one, make it the fullsize of the disk, and then create it. You should have filesystem options when creating it, too.

Dr Small

OK, thanks.

So where it says 'msdos' in the screenshot, that shouldn't be of concern to me?

---

### Post by L Campbell on 2007-12-13
> **L Campbell said:**
> OK, thanks.

So where it says 'msdos' in the screenshot, that shouldn't be of concern to me?

Well, I took a shot at it and then ran the commands:-

tail -f /etc/mtab
cat /etc/fstab
 sudo fdisk -l

qwer@qwer-desktop:~$ tail -f /etc/mtab

/dev/sda1 / ext3 rw,errors=remount-ro 0 0

proc /proc proc rw,noexec,nosuid,nodev 0 0

/sys /sys sysfs rw,noexec,nosuid,nodev 0 0

varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0

varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0

udev /dev tmpfs rw,mode=0755 0 0

devshm /dev/shm tmpfs rw 0 0

devpts /dev/pts devpts rw,gid=5,mode=620 0 0

lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0

securityfs /sys/kernel/security securityfs rw 0 0

.........................................................
qwer@qwer-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=ad88ec7d-a2db-4324-ba39-1b65aa41ef03 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda5

UUID=7d67798c-2298-4f5d-b210-b99cf27e7bf8 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

.....................................................
qwer@qwer-desktop:~$ sudo fdisk -l

[sudo] password for qwer:



Disk /dev/sda: 41.1 GB, 41110142976 bytes

255 heads, 63 sectors/track, 4998 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xf1121ebf



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        4787    38451546   83  Linux

/dev/sda2            4788        4998     1694857+   5  Extended

/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris



Disk /dev/sdb: 4244 MB, 4244636160 bytes

255 heads, 63 sectors/track, 516 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00069633



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1         516     4144738+  83  Linux


I have my fingers crossed.    :-)
........................

---

### Post by L Campbell on 2007-12-13
Thanks very much for ALL the help.

The flash drive is now working normally as far as I can tell.

Kind regards.

---

### Post by Dr Small on 2007-12-13
Good. I'm glad everything worked out properly :D

Dr Small

---

