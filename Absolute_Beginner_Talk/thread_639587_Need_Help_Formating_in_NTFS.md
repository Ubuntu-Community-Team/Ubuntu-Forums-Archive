---
title: "Need Help Formating in NTFS"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by jamelb on 2007-12-13
I am having issues formating a drive in ntfs format? I have an extra hard drive in my case and i wanted to format it in ntfs but i havre not firgured out how. I have downloaded gparted and every time i start it up it says no device found. If i try and use the built in partation manger it will not let me choose ntfs? Any help would be greatly apperciated. 

Also i was wonder if nfs partation would be ok as well. I want to be able to read and write from a windows machine. If thats is possiable than i could go that route as well.

---

### Post by thelatinist on 2007-12-13
It sounds like your machine is not recognizing your new hard disk.  Have you checked in your bios to see if it's there?  If it isn't, then it could be a loose cable or an incorrect jumper setting.

---

### Post by jamelb on 2007-12-13
my bios see's it and during instalation I could have formated it but now it will not let me do it

---

### Post by pwaldo on 2007-12-13
Please post the results of the following commands:
```
mount
```This will show what you currently have mounted (to make sure that the format does not step on your Linux disk).
```
sudo fdisk -l /dev/[s,h]d[a-d]
```
This will print the partition layout of the first four IDE and first four SATA/SCSI disks.

Once we have these, I can tell you the command to format the drive as NTFS

---

### Post by jamelb on 2007-12-13
mount-----
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

sudo fdisk -l /dev/[s,h]d[a-d]------
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 524 MB, 524091392 bytes
255 heads, 63 sectors/track, 15 cylinders 
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/hdc doesn't contain a valid partition table

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06052362

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       19103   153444816   83  Linux
/dev/hdd2           19104       19457     2843505    5  Extended
/dev/hdd5           19104       19457     2843473+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System

it is the 200gig hard drive that i want to format

---

### Post by stchman on 2007-12-13
> **jamelb said:**
> I am having issues formating a drive in ntfs format? I have an extra hard drive in my case and i wanted to format it in ntfs but i havre not firgured out how. I have downloaded gparted and every time i start it up it says no device found. If i try and use the built in partation manger it will not let me choose ntfs? Any help would be greatly apperciated. 

Also i was wonder if nfs partation would be ok as well. I want to be able to read and write from a windows machine. If thats is possiable than i could go that route as well.

Install Gnome Partiton editor on your system assuming you are running Ubuntu as we speak.

```
sudo apt-get -y install gparted
```

When that is done bring gparted up and select your new disk.  You can format it in any file system you wish.

---

### Post by logos34 on 2007-12-13
> **stchman said:**
> Install Gnome Partiton editor on your system assuming you are running Ubuntu as we speak.

```
sudo apt-get -y install gparted
```

When that is done bring gparted up and select your new disk.  You can format it in any file system you wish.

The OP just said he tried the installed gparted and it won't let him choose ntfs format.

Now that we know the drive, try:

sudo apt-get install ntfsprogs

sudo mkntfs -v /dev/sda

(--> this will do a full format and repair any bad sectors)

---

### Post by jamelb on 2007-12-13
it gave me 
/dev/sda is an entire device, not just one partition 
refusing to make filesystem here

---

### Post by logos34 on 2007-12-13
oops, typo

/dev/sda1

---

### Post by jamelb on 2007-12-13
it said 

the device doesnt exist did u specify it correctly

---

### Post by monte48lowes on 2007-12-13
You must first create a partition. You can use gparted to create a partition and format that partition as vfat or ext3 or ext2. Then use the:

```
sudo mkntfs -v /dev/sda1
```

or you can use fdisk instead of gparted

```
sudo fdisk /dev/sda
```

type 'n' (creates new partition)
type 'p' (makes partition a primary partition)
type '1' (makes it the first partition)

You can then use the defaults for starting and ending block to create the partition across the whole drive. Or possibly make two partitions if you wish.

type 'w' to write out the partition

type 'x' to exit.

Then you can format that partition using the above mkntfs command.

Mike

---

### Post by monte48lowes on 2007-12-13
Just a quick note:

I often want to know what drives the kernel is seeing. I will use

```
ls /dev
```

to see what is happening with my 'sd' devices. For example, I will list (ls) the drives available before plugging in a usb thumb drive. Then after plugging it in I will list (ls) the drives available. I can then see what got added with the new drive being plugged in. From this I can determine what partitions are available on the drive and other useful information.

Mike

---

### Post by stchman on 2007-12-13
> **logos34 said:**
> The OP just said he tried the installed gparted and it won't let him choose ntfs format.

Now that we know the drive, try:

sudo apt-get install ntfsprogs

sudo mkntfs -v /dev/sda

(--> this will do a full format and repair any bad sectors)

The gparted that you can install in Ubuntu via synaptic does support NTFS partition creation and format.  I know it does as I have done it NUMEROUS times.  I have done this with SATA, PATA and drives connected via USB.

---

### Post by jamelb on 2007-12-13
thank you so much to everybody out there that helped no does anybody know how i would mount that hard drive? it is sda

---

### Post by pwaldo on 2007-12-13
You need to run```
 sudo fdisk /dev/sda
```
Then,
[LIST=1]
[*]Type "n" for a new partition[*]Type "p" for primary
[*]Type 1 for the first partition
[*]Select its size
[*]Type "t" for partition type
[*]Select "7" for NTFS
[*]Press "w" to write the changes
[/LIST]

Now do ```
sudo mkntfs -v /dev/sda
```

---

### Post by logos34 on 2007-12-13
> **stchman said:**
> The gparted that you can install in Ubuntu via synaptic does support NTFS partition creation and format.  I know it does as I have done it NUMEROUS times.  I have done this with SATA, PATA and drives connected via USB.

I never said it didn't.  I've done it many times too.  But for some reason it was not allowing the OP to select ntfs.

---

