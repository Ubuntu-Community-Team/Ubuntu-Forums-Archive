---
title: "How to format an external usb hard drive"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by leep on 2007-04-02
Hi,
i performed a search but was not able to find an answer. I got a 80GB external usb drive, I want to format it but I cannot do this using GParted. Here are the steps I follow:

1. plug the usb cable
2. switch the drive on
3. an icon appears on my desktop
4. i unmount the drive
5. i open gparted, and i can see it
6. i select to remove all partitions and to format it to vfat32
7. the process starts, but once it writes the new partition info, before he starts the format process, the disk is auto-mounted again, so the process fails.

Someone could help me?
Thanks in advance,
Simone

---

### Post by crispy_420 on 2007-04-02
bump!

I would like to know how to as well. Maybe the GParted LiveCD?

---

### Post by devnulljp on 2007-04-03
Use fdisk and mkfs on the command line
plug in the drive
dmesg will show you where it is, probably something like /dev/sda
sudo fdisk /dev/sda
type m will give you instructions
basically 'c' will create a partition
follow the instructions
sudo mkfs -t <type> /dev/sda1   where type is vfat or ext2 or ext3 etc.
try man fdisk
and 
man mkfs

---

### Post by question_chick on 2007-04-03
I am having the same problem.

Does anyone have a solution that still lets me use gparted? I don't have anything against the command line but I would prefer to be able to parition drives via a graphical interface.

---

### Post by Bias on 2007-04-06
> **devnulljp said:**
> Use fdisk and mkfs on the command line
plug in the drive
dmesg will show you where it is, probably something like /dev/sda
sudo fdisk /dev/sda
type m will give you instructions
basically 'c' will create a partition
follow the instructions
sudo mkfs -t <type> /dev/sda1   where type is vfat or ext2 or ext3 etc.
try man fdisk
and 
man mkfs

Thanks for that, solved my problem. I had an unpartioned disk in my USB drive, the fdisk didn't work though didn't seem to have any command to create a partition, 'c' did something with DOS that I didn't fully comprehend.

dmesg, did not seem to show the drive but by looking in the /dev directory at the sda file then removing the USB drive and watching the file vanish I satisfied myself it was the right one :)

didn't need the man commands, sudo worked fine with mkfs and seeing as I wanted just one partition on the drive the fdisk problem didn't matter.

Thanks again,

Nick.

---

### Post by vanadium on 2007-04-07
Few, I installed Ubuntu yesterday, and this thread helped me to convert my USB drive to fs3. Overall, it&#347; more daunting than right-clicking the drive and selecting "Format" as with the "competition".

I was helped by dmesg to identify the drive, depite the fact that the command trows pages of information in your face:

```

....
[17235346.476000]   Vendor: TOSHIBA   Model: MK8025GAS         Rev: KA02
[17235346.476000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17235346.476000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[17235346.480000] sdb: Write Protect is off
[17235346.480000] sdb: Mode Sense: 53 00 00 08
[17235346.480000] sdb: assuming drive cache: write through
[17235346.480000] S
....

```
I had a hard time recognizing it, but it is indeed the "sdb" that signalled that my drive was mounted in /dev/sdb

The drive was NTFS formatted, thus was already partitioned: the use of fdisk was not needed. I could format the drive with the command

mkfs -t ext3 /dev/sdb1

the "1" after /dev/sdb1 presumably refers to "partition 1".

Do not mount the drive immediately from right-clicking in the file browser. i found that the drive would only be mounted after first breaking the USB connection and then connecting it again.

---

### Post by 3rdalbum on 2007-04-07
If you still want to use Gparted, do this:

```
sudo apt-get install openbox
```

Log out, choose Options menu and then Sessions... and choose the Openbox session.

Log in, then right-click on the brown desktop and open the terminal. Type "gksudo gparted". Now you won't get the drive automounting problem.

---

