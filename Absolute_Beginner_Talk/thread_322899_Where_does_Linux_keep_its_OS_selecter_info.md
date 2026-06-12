---
title: "Where does Linux keep its OS selecter info?"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-12-21
When installing, Linux install a Boot OS selecter. Where does it keep these files?
If its on the Linux partition, i probably won't have a problem. I am wiping my Window installation, and its main partition. If i did that, then re-installed Windows XP, Would Linux still be bootable, and all files, and OS Selecter still be intact and operational?

---

### Post by LookTJ on 2006-12-21
I'm not sure what you mean, but don't you mean Grub?

---

### Post by Bachstelze on 2006-12-21
The boot informations are stored in two places (by default) : the main GRUB files are indeed stored in your Linux partition but there's also a part of it in your MBR, that's the one Windows will wipe out during installation. It's fairly easy to [recover it](https://wiki.ubuntu.com/RecoveringGrub) though.

---

### Post by Captain Kirk76 on 2006-12-21
In the recovery manual it says this.

At this stage you are presented with a screen where you can select which partition is your root partition (there is a list of the partitions on your hard drive, so you are required to know which partition number Ubuntu is on). This will be dev/discs/disc0/partX, where the X is a partition number.

How can i tell which partition its on? (My 2 Hard Drives are split into about 8 partitions all together, only two are Linux, a swap and a main partition for Linux files)

---

### Post by LookTJ on 2006-12-21
on the live cd, open a terminal and type sudo fdisk -l

---

### Post by Captain Kirk76 on 2006-12-21
When i type rescue i get this error.

"could not find kernel image"
:(

Please help me, i really want Ubuntu back...

---

### Post by Captain Kirk76 on 2006-12-21
Bump!

---

### Post by Bachstelze on 2006-12-21
See the link I gave yous in my last message.

---

### Post by Captain Kirk76 on 2006-12-21
I did!
It gives me this error when i type rescue!

[quote=Myself]
When i type rescue i get this error.

"could not find kernel image"


Please help me, i really want Ubuntu back...
[/quote]

---

### Post by BarfBag on 2006-12-21
Grub (the "OS selector" or boot loader) is usually stored on the MBR (master boot record).  Removing the Windows partition shouldn't cause any harm to your system, but reinstalling it will.  Windows Setup wipes the MBR as it's installing.  While your Ubuntu partition will still be there, Grub will be missing.  You'll have to reinstall it.

---

### Post by Captain Kirk76 on 2006-12-21
I know that.... but how.
every method doesnt work.

---

### Post by Bachstelze on 2006-12-21
All right, try this :

0. Boot from a Live CD and open up a terminal.

1. Become root : *sudo -i*

2. Create a mountpoint for your partition : *mkdir /mnt/root*

3. Mount it : *mount -t ext3 /dev/foo /mnt/root*

3b. If you have a separate /boot partition, mount it too : *mount -t ext3 /dev/bar /mnt/root/boot*

4. Install GRUB : *grub-install --root-directory=/mnt/root /dev/baz*

5. Reboot :)


*P.S. : If you don't know what to put instead of foo/bar/baz, post the output of *sudo fdisk -l* and we'll tell you.*

---

### Post by Captain Kirk76 on 2006-12-21
The command you told me to do is not working.

> ubuntu@ubuntu:~$ sudo fdisk -|
>

---

### Post by Bachstelze on 2006-12-21
Its a lowercase L (for **l**ist), not an uppercase i, a | or whatnot :)

---

### Post by Captain Kirk76 on 2006-12-21
here we go :D

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hdc2            6375        9964    28836675    f  W95 Ext'd (LBA)
/dev/hdc5            6375        9964    28836643+   7  HPFS/NTFS

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               2       21488   172594327+   f  W95 Ext'd (LBA)
/dev/hdd2           21489       26690    41785065   83  Linux
/dev/hdd3           26691       26951     2096482+  82  Linux swap / Solaris
/dev/hdd4           26952       30401    27712125    7  HPFS/NTFS
/dev/hdd5               2        8355    67103473+   7  HPFS/NTFS
/dev/hdd6            8356       21488   105490791    7  HPFS/NTFS

---

### Post by teet on 2006-12-21
> **Captain Kirk76 said:**
> The command you told me to do is not working.

>

sudo fdisk -l

sudo fdisk -|

It appears as if you're using the straight line bar thing "|" instead of an L (i.e. "l")

l|l|l|l|l|l|l|

They're different.

You're going to need to follow the steps HymnToLife provided.  I just did what you are doing a few months ago (reinstalled XP) and had to run the grub-install command to fix grub.

-teet

---

### Post by Bachstelze on 2006-12-21
All right, use /dev/hdd2 in step 3, skip 3b and /dev/hdc in step 4.

---

### Post by Captain Kirk76 on 2006-12-21
on 3 i get this error.
I have included the entire details of what i did for steps 1 & 2 too.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /mnt/root
root@ubuntu:~# mount -t /dev/hdd2 /mnt/root
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
root@ubuntu:~#

---

### Post by Bachstelze on 2006-12-21
> **HymnToLife said:**
> 
3. Mount it : *mount -t **ext3** /dev/foo /mnt/root*

Read more carefully, a typo when running things as root can wipe out your entire system ;) (it was not the case here though, don't worry)

---

### Post by Captain Kirk76 on 2006-12-21
I don't get this in Step 4, what does it mean? It worked, or it didnt?

root@ubuntu:~# mount -t ext3 /dev/hdd2 /mnt/root
root@ubuntu:~# grub-install --root-directory=/mnt/root /dev/hdc
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hdc
(hd1)   /dev/hdd
root@ubuntu:~#

---

### Post by Bachstelze on 2006-12-21
Yes, it worked, you can reboot now :)

---

### Post by Captain Kirk76 on 2006-12-21
It works, Thanks alot!

---

