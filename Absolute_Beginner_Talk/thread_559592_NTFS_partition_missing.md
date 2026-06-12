---
title: "NTFS partition missing"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by NorthernPaladin on 2007-09-25
My ntfs partition is missing. I shrunk my linux partition couple days ago so I could test if I can install windows(there is something wrong with mbr so it wont boot). Anyway, windows did not work, I then restored grub from Live-cd but now my ntfs partition does not show and it has(or had) about 30Gb of data. I do not know what is the problem. Could anybody help?

---

### Post by ddrichardson on 2007-09-25
Output of fdisk -l?

---

### Post by meindian523 on 2007-09-25
Was it visible earlier.try apt-get ting ntfs-3g,ntfs-config and retrying.Oh BTW,don't forget to add yourself to the FUSE group after installing the above......

---

### Post by NorthernPaladin on 2007-09-25
fdisk -l gives nothing. It was visible and I had read/write acces to it before(got it with automatix). Is it possible that the ntfs partition is so corrupted that linux wont recognize it? When I tried to shrunk it with gparted it gave an error(don't remember the exact text, something that it was inconsistent), so I shrunk the linux partition.

---

### Post by ezze66 on 2007-09-27
Hey! I'm new in the Ubuntu OS. I have a dual boot with MS Windows XP on one of my hard drives, and Ubuntu on another hard drive. Installation of Ubuntu is fine and working, startup (GRUB) will not show WIN XP on the list to boot, so I have to boot WIN XP by startup menu pressing (F8 or DEL).

the output of** fdisk -l **only shows the partition on which Ubuntu is istalled on HD2 but will not show my NTFS partition on HD1.

any help please.
thanks!

=)

---

### Post by YoshiHNS on 2007-09-27
just out of curiosity, do you have both an ide drive and sata?

---

### Post by ezze66 on 2007-09-27
First HD is SATAII (two partitions, WIN XP and My files) 160 GB

Second HD is IDE (3 partitions for Ubuntu, root, swap, and home) 30 GB

---

### Post by LowSky on 2007-09-27
> **ezze66 said:**
> First HD is SATAII (two partitions, WIN XP and My files) 160 GB

Second HD is IDE (3 partitions for Ubuntu, root, swap, and home) 30 GB

Thats the same setup I have, and mine lists both OSes fine.

try this
[http://www.linuxforums.org/forum/ubuntu-help/68350-add-windows-grub.html]("http://www.linuxforums.org/forum/ubuntu-help/68350-add-windows-grub.html")

---

### Post by ezze66 on 2007-09-28
this is my error:


ezequiel@ezequiel-desktop:~$ sudo apt-get install ntfs-3g
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


any help?

---

### Post by meindian523 on 2007-09-29
were you running Synaptic or Update Manager simultaneously?If yes,that's your problem....Only 1 software manager/installer can be running at a time whether GUI or CLI....

---

### Post by ddrichardson on 2007-09-29
If you are sure that nothing else is running, then you can delete the lock file.```
sudo rm /var/lib/dpkg/lock
```

---

### Post by louieb on 2007-09-29
> **NorthernPaladin said:**
> fdisk -l gives nothing. 
Try **sudo fdisk -l** if that gives nothing then you got a real problem. Like no hard drives. And post the output. I need to see for myself.

---

### Post by ezze66 on 2007-09-29
this is what appears while trying to install ntfs-3g via CLI:

ezequiel@ezequiel-desktop:~$ sudo apt-get install ntfs-3g
Password:
Reading package lists... Done
Building dependency tree... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up fuse-utils (2.6.3-0givre2) ...
creating fuse device node...
/sbin/MAKEDEV: don't know how to make device "fuse"
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ntfs-3g:
 ntfs-3g depends on fuse-utils (>= 2.6); however:
  Package fuse-utils is not configured yet.
dpkg: error processing ntfs-3g (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ntfs-config:
 ntfs-config depends on ntfs-3g; however:
  Package ntfs-3g is not configured yet.
dpkg: error processing ntfs-config (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fuse-utils
 ntfs-3g
 ntfs-config
E: Sub-process /usr/bin/dpkg returned an error code (1)


this is the output of my sudo fdisk -l

ezequiel@ezequiel-desktop:~$ sudo fdisk -l

Disk /dev/hdd: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1391    11173176   83  Linux
/dev/hdd2            1392        1522     1052257+  82  Linux swap / Solaris
/dev/hdd3            1523        3738    17800020   83  Linux

---

### Post by ezze66 on 2007-09-29
bump

please need help

---

### Post by louieb on 2007-09-29
> **ezze66 said:**
> bump....

Weirdest fdisk output I've seen in a long time. Shows you only have 1 hard drive. Nothing strange about that but the fact that is shows up as  **hdd **is odd where are hda, hdb, and hdc? Are they optical drives (CD or DVD)?

1st thing you should do is check you BIOS setup make sure your type is set to auto and the mode is set to LBA (IDE drives only not sure about SATA drives). Just wonderinf if your BIOS setup sees your SATA drive?

---

### Post by ezze66 on 2007-09-30
Primary IDE Master > CDW/DVD 
Primary IDE Slave   >  None

Secondary IDE Master > None
Secondary IDE Slave   > Maxtor 30GB ( hdd ) ubuntu is intalled here with 3 partitions

SATA 1 > Western Digital 160GB NTFS Winxp 2 partitions
SATA 2 > None

the SATA hard disk appears on my Bios, but ubuntu will not recognize it.
=(

---

### Post by ezze66 on 2007-10-01
bump-....

any help please.

---

### Post by ezze66 on 2007-10-04
help please.

what do i need in order to see my sata disk?

i try with MEPIS and it works fine. mepis detected my ntfs sata disk.
why not ubuntu?

how can i uninstall ntfs-3g ? and reinstall ntfs-3g ??

---

### Post by louieb on 2007-10-04
Which version of Ubuntu did you install? If it was 7,10 Gutsy you have to remember it just went Beta and still has bugs. If it was 7.04 Feisty the sounds like a bad install. I'd probably download   and burn and install again. Since MEPIS works  I'm inclined  to think there is something wrong with you install 
This might help fix your ntfs-3g package problem. 
[http://ubuntuforums.org/showthread.php?t=565837](http://ubuntuforums.org/showthread.php?t=565837)

---

### Post by American_Outcast on 2007-10-04
Let me show you how my fdisk -l looks and maybe it will assist you or others in figuring this out. I have two NTFS partitions and one fat32 partition. I set up three Windows partitions after I had installed Ubuntu and I had to resize sda1 and create sda2 for NTFS. However I had to disconnect two hard drives to install XP because it kept trying to write to hda's master boot record and it couldn't. After I installed XP I connected the IDE and SATA drive back up, edited the grub file (menu.lst) and it works fine. 

> $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18173   145974591   83  Linux
/dev/sda2           18174       19457    10313730    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         612     4915858+  82  Linux swap / Solaris
/dev/hda2             613        5499    39254827+  83  Linux
/dev/hda3            5500        9729    33977475   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         672     5397808+   b  W95 FAT32
/dev/hdb2   *         673        9728    72742320    7  HPFS/NTFS


---

### Post by LowSky on 2007-10-04
> **ezze66 said:**
> Primary IDE Master > CDW/DVD 
Primary IDE Slave   >  None

Secondary IDE Master > None
Secondary IDE Slave   > Maxtor 30GB ( hdd ) ubuntu is intalled here with 3 partitions

SATA 1 > Western Digital 160GB NTFS Winxp 2 partitions
SATA 2 > None

the SATA hard disk appears on my Bios, but ubuntu will not recognize it.
=(

I think its odd that your Hard drive is on the Secondary IDE not to mention on the slave... usually they are on the Primary Master... just a thought.

What happens if you unplug you IDE hard drive, can you then boot into Windows?

---

