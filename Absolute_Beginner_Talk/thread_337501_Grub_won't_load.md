---
title: "Grub won't load"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by mickd1337 on 2007-01-13
Ok. Had a previous windows xp installation, bought a new hdd, tried installing ubuntu and it straight up loads windows xp. I used the ubuntu efty desktop install for 32 bit x86. My configuration is as follows:

sda 250gb hdd
sda1 ext3 with ubuntu
sda3 linux-swap
sda2 extended
sda5 unformatted partition

sdb 200gb hdd
sdb1 ntfs with winxp
sdb2 extended
sdb5 ntfs storage

I chose the automatic install of grub to (hd0) on the desktop cd.

Any help would be much appreciated.

---

### Post by ajmorris on 2007-01-13
so it does not load GRUB at all?

---

### Post by mickd1337 on 2007-01-13
Nup it goes straight to the windows loading screen.
Is there some bios thing i have to do?

---

### Post by ajmorris on 2007-01-13
Ok, load the live cd and mount your linux partition with write privilages.

(cd /media [enter] sudo mount -w sda1 [enter] (or hda1 which ever one live cd will recognise))

then run "sudo grub" [enter]

in grub type "root (hd0,0)" [enter]     this is setting your linux partition as the root partition (it is hd0,0 because it is on your first hard disk and on your first partition, "sda1 ext3 with ubuntu")

then type "setup (hd0)" [enter]

This should work fine. :)

---

### Post by mickd1337 on 2007-01-13
ubuntu@ubuntu:/media$ sudo mount -w sda1
mount: can't find sda1 in /etc/fstab or /etc/mtab

Do i need to edit fstab? I forgot how to do that.

Thanks.

---

### Post by ajmorris on 2007-01-13
do an ls in /media. Probably is hda1 instead.

if neither work do "sudo gedit /etc/fstab" to find out what your linux partition is mounted as.

---

### Post by mickd1337 on 2007-01-13
This is what fstab says:
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by ajmorris on 2007-01-13
what folders were in /media? You are running the ubuntu live cd aren't u?

---

### Post by mickd1337 on 2007-01-13
No folders were in media. Yes i am running the ubuntu live cd.

---

### Post by ajmorris on 2007-01-13
run "sudo grub"
then type "find /boot/grub/stage1"

---

### Post by mickd1337 on 2007-01-13
It says (hd0,0)
Which i assume is the ext3 linux part.

---

### Post by ajmorris on 2007-01-13
yes. So while in "sudo grub"
type "root (hd0,0)"
then "setup(hd0)"

That should do the trick.

---

### Post by mickd1337 on 2007-01-13
I think i already did that and received the same problem. I will try it again. *An atheist praying*

---

### Post by mickd1337 on 2007-01-13
Yeh it didnt work, Went straight to windows again. Spewing.

---

### Post by ajmorris on 2007-01-13
yeah until you can mount the linux partition it won't work

sda1 or hda1 should work if that's what partition it is on.

Do you have more than one hard disk?

---

### Post by ajmorris on 2007-01-13
nevermind i just realised u do.

Is it possible linux is on your second and windows in on your first?

---

### Post by ajmorris on 2007-01-13
what happens if you type "sudo fdisk -l" on the live cd?

---

### Post by mickd1337 on 2007-01-13
I am going by what gparted says. Is there another way of checking?

---

### Post by ajmorris on 2007-01-13
sudo fdisk -l should tell you.

if it is on the second hard drive linux will be sdb1 or hdb1. But gparted should be right. Try it anyway though. There will be a way to mount your linux partition. And what you tried should have worked.

---

### Post by mickd1337 on 2007-01-13
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda2            3443       30401   216548167+   5  Extended
/dev/sda3            3188        3442     2048287+  82  Linux swap / Solaris
/dev/sda5            3443       30401   216548136    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       24320   169750822+   f  W95 Ext'd (LBA)
/dev/sdb5            3188       24320   169750791    7  HPFS/NTFS

---

### Post by rai4shu2 on 2007-01-13
I generally find that you need to do "grub-install" to get the grub MBR installed. For example:

sudo mount /dev/hda1 /mnt/hda1
sudo /sbin/grub-install --root-directory=/mnt/hda1 /dev/hda

---

### Post by ajmorris on 2007-01-13
in /media "sudo mount -w sda1" should mount it with write permissions. I can't think why it says it is not in /etc/fstab. You might have to add the entry manually.

---

### Post by ajmorris on 2007-01-13
to add the entry add:

/dev/sda1       /media/sda1              ext3 notail         0       1

This entry will not stay in the live cd's /etc/fstab after a reboot however.

After adding this entry try mounting the partition again.

---

### Post by ajmorris on 2007-01-13
yeah grub-install does work but i always do it this way to re-install/install grub.

But it should be /media/hda1 not /mnt/hda1.

---

### Post by mickd1337 on 2007-01-13
Ok, well "sudo mount /dev/hda1 /mnt/hda1" does not work "mount point does not exist". With sda1 aswell.

and

sudo mount -w sda1
mount: can't find sda1 in /etc/fstab or /etc/mtab

so how do i edit the fstab?

---

### Post by rai4shu2 on 2007-01-13
You need to do this first:

sudo mkdir /mnt/hda1

before you can use that as a mount point.

---

### Post by ajmorris on 2007-01-13
> **mickd1337 said:**
> Ok, well "sudo mount /dev/hda1 /mnt/hda1" does not work "mount point does not exist". With sda1 aswell.

and

sudo mount -w sda1
mount: can't find sda1 in /etc/fstab or /etc/mtab

so how do i edit the fstab?

yeah the folder needs to be created. But use /media not /mnt.

In a previous post i posted how to edit your fstab.

---

### Post by mickd1337 on 2007-01-13
> 
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo /sbin/grub-install --root-directory=/mnt/sda1 /dev/sda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/sda1/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/sda1/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/sda1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb


Reckon this will work?
Thanks for help.

---

### Post by ajmorris on 2007-01-13
yes that should work. :)

---

### Post by ajmorris on 2007-01-13
but shouldn't it be sudo /sbin/grub-install --root-directory=/mnt/sda1 /dev/**sda1**

not sudo /sbin/grub-install --root-directory=/mnt/sda1 /dev/sda

---

### Post by rai4shu2 on 2007-01-13
No, /dev/sda was correct.

---

### Post by ajmorris on 2007-01-13
why is it /dev/sda when mickd's linux is on sda1?

---

### Post by Kirky_D on 2007-01-13
If you had windows installed first, then installed ubuntu on another drive, then the grub menu will be put in the mbr of that new drive.

So in bios you need to change the boot order so that your new drive boots up first, which will load grub, then you can select either ubuntu or windows.

Hope that helps

---

### Post by rai4shu2 on 2007-01-13
The grub-install can only install to the MBR of the device, not to a particular partition.

---

### Post by mickd1337 on 2007-01-13
I did it with sda1 aswell. Still nothing. WIth some bios, you cant choose the particular hdd to boot from. I will have a look (this is my friends comp). I might shoot myself now though.

---

### Post by Kirky_D on 2007-01-13
You mis-understood what I said.

He has Windows installed on one hard drive.

He installed ubuntu on a completely seperate hard drive.

therefore grub would be installed on this seperate hard drive.

So if you boot from this seperarte hard drive before the windows one, grub will appear.

---

### Post by mickd1337 on 2007-01-13
Cheerz fellaz. Changing hdd boot sequence worked. Thank the god who doesn't exist!

---

### Post by Kirky_D on 2007-01-13
No worries! Glad to help

---

