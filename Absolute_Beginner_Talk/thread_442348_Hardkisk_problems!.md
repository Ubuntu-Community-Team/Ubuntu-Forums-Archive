---
title: "Hardkisk problems!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-13
Before Installed utunbu 7.0.4, I had 4 partitions. Which was C:,d:,e:,f. 

and after I installed utunbu, C and E was joined together, and D drive is now locked so I can't

write something such as to put any files to the d drive! I only can read! so I tried on

root, and tried to change the owner because if I try to change the D drive's setup to 

deactive write protection, it will say I can't because I'm not the owner.

So I tried to change the owner, but then it will say I can't because it's read-only disk,

it's driving me crazy now...and my F drive, I can't even find where my F drive is!

this is pretty weird..and I'm so stressed out right now...I was on the computer for the whole

weekend...:'(

can anyone please help me?

---

### Post by annda on 2007-05-13
the D disk is NTFS, which is read-only by default in Linux. if you want to write to it, read this guide:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

in order to see what partitions you have on your disk, please go to terminal and type this command:
```

sudo fdisk -l
```

(this is small L)

copy (in the terminal: select with the mouse, ctrl+shift+c) and paste the result here.

---

### Post by Acksys on 2007-05-13
Now that you're using Linux, you might want to stop thinking in terms of drive letters - they're called partitions.

If the partition you're trying to write to is NTFS, that's the reason you can't write to it - NTFS partitions are read-only by default. If you've completely switched from Windows, your best option (in my opinion) is to convert the partition to FAT32, which is readable and writable from Linux (back up the data first).

gparted is a user-friendly partitioning tool that should already be installed on your system, if you wish to use it to do this conversion.

Try reading these:

[http://tldp.org/HOWTO/Partition/intro.html](http://tldp.org/HOWTO/Partition/intro.html) (some information about disk partitions in general)
[http://tldp.org/HOWTO/Filesystems-HOWTO.html](http://tldp.org/HOWTO/Filesystems-HOWTO.html) (info about how Linux handles different filesystems)

Make some coffee, relax, and don't be afraid to ask us for help with these issues.

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> the D disk is NTFS, which is read-only by default in Linux. if you want to write to it, read this guide:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

in order to see what partitions you have on your disk, please go to terminal and type this command:
```

sudo fdisk -l
```

(this is small L)

copy (in the terminal: select with the mouse, ctrl+shift+c) and paste the result here.

Thank you for the response!

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15197   122069871    7  HPFS/NTFS
/dev/sdb2           15198       30401   122126130    f  W95 Ext'd (LBA)
/dev/sdb5           15198       30401   122126098+   7  HPFS/NTFS

---

### Post by annda on 2007-05-13
it looks like you have linux on the first disk

/dev/sda1 * 1 9331 74951226 83 Linux **- your ubuntu system**
/dev/sda2 9332 9733 3229065 5 Extended
/dev/sda5 9332 9733 3229033+ 82 Linux swap / Solaris - **swap on an extended partition**

and windows on the second:

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 15197 122069871 7 HPFS/NTFS **- your windows system**
/dev/sdb2 15198 30401 122126130 f W95 Ext'd (LBA)
/dev/sdb5 15198 30401 122126098+ 7 HPFS/NTFS **- your extra files on an ntfs/windows partition**

can you tell us again what partition is missing and from which disk? have you lost any files or is the disk layout just not what you expected?

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> it looks like you have linux on the first disk

/dev/sda1 * 1 9331 74951226 83 Linux **- your ubuntu system**
/dev/sda2 9332 9733 3229065 5 Extended
/dev/sda5 9332 9733 3229033+ 82 Linux swap / Solaris - **swap on an extended partition**

and windows on the second:

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 15197 122069871 7 HPFS/NTFS **- your windows system**
/dev/sdb2 15198 30401 122126130 f W95 Ext'd (LBA)
/dev/sdb5 15198 30401 122126098+ 7 HPFS/NTFS **- your extra files on an ntfs/windows partition**

can you tell us again what partition is missing and from which disk? have you lost any files or is the disk layout just not what you expected?

I think it's dev/sdb5..!

and I didn't lose any files I think...when C:\ and E:\ was joined, they got formatted and thats it..

thank you for the response!

---

### Post by annda on 2007-05-13
first make sure that the partition isn't mounted yet (meaning: already connected to ubuntu) - go to the media folder and see if sdb5 is there. if it is, click on it to see if it shows any files.

if sdb5 is not there, or it is empty, you will have to use [this guide]("http://www.psychocats.net/ubuntu/mountwindows") to include it in your configuration and mount it when the system boots.

post back with any questions.

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> first make sure that the partition isn't mounted yet (meaning: already connected to ubuntu) - go to the media folder and see if sdb5 is there. if it is, click on it to see if it shows any files.

if sdb5 is not there, or it is empty, you will have to use [this guide]("http://www.psychocats.net/ubuntu/mountwindows") to include it in your configuration and mount it when the system boots.

post back with any questions.

thank you for the response!

I found the folder name "And so on" which is the drive's name. but it's not hard disk form tho..

It's just folder form...

---

### Post by annda on 2007-05-13
one more try before you have to use the guide i mentioned - if you go to places>computer in the menus, do you see your sdb5? if so, can you mount it using the context menu (right-click)?

if it's mounted, do you see your files when you open it?

even if it works, you will heve to do it every time after reboot, unless you change your configuration to mount it on boot...

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> one more try before you have to use the guide i mentioned - if you go to places>computer in the menus, do you see your sdb5? if so, can you mount it using the context menu (right-click)?

if it's mounted, do you see your files when you open it?

even if it works, you will heve to do it every time after reboot, unless you change your configuration to mount it on boot...

no..it's not there..I don't see sdb5..:'(

---

### Post by heiko.nolen on 2007-05-13
> **annda said:**
> if sdb5 is not there, or it is empty, you will have to use [this guide]("http://www.psychocats.net/ubuntu/mountwindows") to include it in your configuration and mount it when the system boots.

At the end of that guide there's a reference to some ntfs tools that are available from the System>Administration>Synaptic Package Manager

I haven't had this problem myself, but found it useful as a n00b to try and use the package managers as much as possible while getting comfortable with the terminal.

You can open the Synaptic Package Manager and simply search for "ntfs" and you'll get at least the following options:

NTFS GNOME virtual filesystem module
ntfs-config
ntfsprogs
testdisk (scanner & disk recovery)

And [here's]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") the straight link to the referred guide

---

### Post by annda on 2007-05-13
this happens because the partition in question is on another disk.

if i understand you right, you have a folder "And so on" in your media folder, but it's empty when you click on it. if that's right, you can try this one-time command in the terminal to mount the partition before you make any lasting changes to your system configuration files:

sudo mount /dev/sdb5 /media/And\ so \on

please copy and paste is (middle-click or ctr+shift+v in the terminal) - capital letters are different from smallcaps in linux and spaces need to be escaped with a backslash.

tell us what is the result of the command. if your system does not complain, your drive is mounted and you can access it from the media folder.

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> this happens because the partition in question is on another disk.

if i understand you right, you have a folder "And so on" in your media folder, but it's empty when you click on it. if that's right, you can try this one-time command in the terminal to mount the partition before you make any lasting changes to your system configuration files:

sudo mount /dev/sdb5 /media/And\ so \on

please copy and paste is (middle-click or ctr+shift+v in the terminal) - capital letters are different from smallcaps in linux and spaces need to be escaped with a backslash.

tell us what is the result of the command. if your system does not complain, your drive is mounted and you can access it from the media folder.

Thank you for the response!

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

I got this..

---

### Post by annda on 2007-05-13
do you have the "And so on" folder in media?

please create a temporary mountpoint to see if the partition works at all:

```
sudo mkdir /media/andsoon
```

also, i did make a mistake - for nfts partitions you need to specify the filesystem, so it should be:

> sudo mount -t ntfs /dev/sdb5 /media/And\ so \on

with the new mountpoint:
```
sudo mount -t ntfs /dev/sdb5 /media/andsoon
```

what happens now?

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> do you have the "And so on" folder in media?

please create a temporary mountpoint to see if the partition works at all:

```
sudo mkdir /media/andsoon
```

also, i did make a mistake - for nfts partitions you need to specify the filesystem, so it should be:



with the new mountpoint:
```
sudo mount -t ntfs /dev/sdb5 /media/andsoon
```

what happens now?

Thank you for the response!

danny@Dan:~$ sudo mkdir /media/andsoon
danny@Dan:~$ sudo mount -t ntfs /dev/sdb5 /media/And\ so \on
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
danny@Dan:~$ sudo mount -t ntfs /dev/sdb5 /media/andsoon


The result..

---

### Post by annda on 2007-05-13
if you didn't get any errors or other messages after this command:

danny@Dan:~$ sudo mount -t ntfs /dev/sdb5 /media/andsoon

navigate to media>andsoon and see if you have all your files there.

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> if you didn't get any errors or other messages after this command:

danny@Dan:~$ sudo mount -t ntfs /dev/sdb5 /media/andsoon

navigate to media>andsoon and see if you have all your files there.

Thank you for the response!

I double clicked the folder, then it says, The folder could not be displayed.

You do not have the permissions necessary to view the contents of "andsoon"

:'(...

---

### Post by annda on 2007-05-13
oops, not so good.

from the terminal again unmount the drive first:

umount /media/andsoon

then open nautilus as root (administrator):

gksu nautilus

navigate to media, right-click andsoon, choose permissions and select "access files" for all threee groups. if you have the option, click on "apply permissions to enclosed files". close and mount the partition again.

---

### Post by rocketboys on 2007-05-13
> **annda said:**
> oops, not so good.

from the terminal again unmount the drive first:

umount /media/andsoon

then open nautilus as root (administrator):

gksu nautilus

navigate to media, right-click andsoon, choose permissions and select "access files" for all threee groups. if you have the option, click on "apply permissions to enclosed files". close and mount the partition again.

Thank you for the response!

I did what you told me to..I can go into the folder now..

---

