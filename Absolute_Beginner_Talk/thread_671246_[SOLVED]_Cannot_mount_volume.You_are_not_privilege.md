---
title: "[SOLVED] Cannot mount volume.You are not privileged to mount this volume."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Desperate on 2008-01-18
After reading and reading for days I finally get this ^^ when I try to mount the volume, I must be close, but something is still missing there. Any Hints??

ubuntu@ubuntu:~$ dmraid -s
ERROR: you must be root
ubuntu@ubuntu:~$ sudo dmraid -s
*** Group superset isw_bccebhcagd
--> Active Subset
name   : isw_bccebhcagd_RAID0  ----------              marked like this in dev/mapper
size   : 468882432
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 2         ----------------------------                          2 scsi disks that's okay
spares : 0
ubuntu@ubuntu:~$ ls -l /media
total 0
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85933d77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29185   234428481    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000108

Disk /dev/sdb doesn't contain a valid partition table
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo gedit /etc/fstab
ubuntu@ubuntu:~$ sudo apt-get -y install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 76 not upgraded.
ubuntu@ubuntu:~$ sudo mount -a
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


DMRaid documentation suggest that you are installing one, I'm trying to save my Data on it after XP pro doesn't want to know it anymore and refuses to boot or restore.
I'm running live disk, so reboot sets me right back to where I was and is no option.

I'm learning more about my computer than I did the last 25 years :lolflag: Sure a hands on experience that Ubuntu :confused:

Checked the disk(s) with NTFS4Dos from the UBCD and all is fine and working as should, I must have wrecked one file too many in Windows/system32 to prevent Billy G from checking in on me ( renamed so if..  I change that back and should be good to go

Any help welcome, thanks for your time

Richard

---

### Post by airbornemist6 on 2008-01-18
are you able to access the disk from a livecd? if not, then the partition is most likely corrupted. If so, then you might be able to use the Windows CD to fix it from recovery console. If that doesn't fix it you can get yourself a copy of an RIP (recovery is possible) linux disk which contains the utilities necessary to fix broken partitions. For more information about that, I'll link you to a thread I made the *first* time i corrupted my NTFS partition.
[http://ubuntuforums.org/showthread.php?t=535673](http://ubuntuforums.org/showthread.php?t=535673)

If your partition is not corrupted, linux might just not be mounting it right, and you can look up how to edit FSTAB to make that work. Unfortunately, for the answer to that question i can't point you towards any specific thread, because I have to go to class in a few minutes xD

If you can't find one, let me know, and I will try and find one for you. You might also want to look for something specifically meant to set up RAID. Since, I assume you have RAID.

---

### Post by Desperate on 2008-01-18
@Airborne
Thanks for the trouble, disk or volume is okay, ntfs4dos has no problems found and can run programs on it  (I just can't access it from there)   :(
The reason windows doesn't boot is software (I wrecked/renamed a file) I'm glad I made the live cd so I can at least get it online and look for options.
Ubuntu 7.1 can see the volume, but mounting is something else :(
I'll search on for a solution then, getting closer, but really understand it ?? Nope :)
Thanks for your time

Richard

---

### Post by Desperate on 2008-01-20
Still stuck very close to the finish I think (all other attempts left my disk unchanged and it is still not doing what it has to, but nothing changed in its failing so I hope I can still get there)

My computer;
Compaq X09 two 3.2 GHz Intel P4 processors
1010.6 MB memory
AND Intel Raid Serial ATA v3.5.0.2568 on 2 SCSI Seagate hard disks in a volume of 223.6 GB and that's where the trouble starts.
I was running XP pro SP2 until the machine refused to boot in windows or run the rescue option. All options under F8 run dead in a blue screen reboot or a system halt. NTFS4dos can read the whole disk and claims nothing wrong there, I ran check disk from the windows directory (in NTFS4dos)and tested it all possible ways with the Ultimate Boot CD, no problem, but it just doesn't get through the windows boot all the way.

Thanks to Ubuntu live CD I'm now trying the Linux options.

The last one from here [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I start trying.

ubuntu@ubuntu:~$ cd
ubuntu@ubuntu:~$ wget [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)
--18:10:46--  [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)
           => `diskmounter'
Resolving media.ubuntu-nl.org... 81.171.100.21
Connecting to media.ubuntu-nl.org|81.171.100.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,864 (4.8K) [text/plain]

100%[====================================>] 4,864         --.--K/s             

18:10:48 (173.64 MB/s) - `diskmounter' saved [4864/4864]

ubuntu@ubuntu:~$ sudo bash diskmounter
By default the disks will be writable only by root and
Do you want to make the disk writable by all users instead? (y/n)
y
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdb doesn't contain a valid partition table
As of Ubuntu 6.04 (Dapper Drake) there is slightly more NTFS writing support
through a very experimental NTFS FUSE module. Using this seems to work but
is NOT recommended. Do you want to use this? [no] 
Not enabling experimental NTFS write support
No usable windows/mac partitions found
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: isw, "isw_bccebhcagd", GROUP, ok, 234441646 sectors, data@ 0
/dev/sdb: isw, "isw_bccebhcagd", GROUP, ok, 234441646 sectors, data@ 0
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85933d77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29185   234428481   fd  Linux raid autodetect

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000108

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 65 MB, 65798144 bytes------------------my memory stick----------
4 heads, 32 sectors/track, 1004 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x0d0c0b0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1004       64240    6  FAT16
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo gedit /etc/fstab ---------------to edit fstab with the extra line "/dev/sda /media/windows ro,auto,user,fmask=0111,dmask=0000"

ubuntu@ubuntu:~$ sudo mount -a
mount: unknown filesystem type 'dmask=0000' so I start looking what went wrong there and change it
ubuntu@ubuntu:~$ sudo gedit /etc/fstab ---------------to edit fstab with the new line "/dev/sda /media/windows ntfs-3g defaults,nls=utf8,umask222 0 0
Yes I really have no idea what I'm doing, I'm just <fill in forum name>

ubuntu@ubuntu:~$ sudo mount -a
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: isw, "isw_bccebhcagd", GROUP, ok, 234441646 sectors, data@ 0
/dev/sdb: isw, "isw_bccebhcagd", GROUP, ok, 234441646 sectors, data@ 0
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_bccebhcagd_RAID0" already active
RAID set "isw_bccebhcagd_RAID01" already active
ubuntu@ubuntu:~$ sudo mount -a
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
** my directory  dev/mapper/ shows three files  control--- isw_bccebhcagd_RAID0---isw_bccebhcagd_RAID01
** I installed NTFS-Config and that lets me set read support for internal and external drives
** when I go to computer I see "My two CD/DVD's, the USB stick (64Mb ;( ) filesystem and a hopeful 223.6 GB Volume" and when I try to mount it it comes with "Cannot mount volume.-- You are not privileged to mount this volume "
** Now would I need the windows password to get through there? And if, HOW??

Thanks for any help and your time to read this

Desperate Richard :)

---

### Post by Desperate on 2008-01-21
Not stopped by any knowledge I seem to make some progress :)

ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_bccebhcagd_RAID0 /media/windows

mount: /dev/mapper/isw_bccebhcagd_RAID0 already mounted or /media/windows busy
So what does that mean? It's not mounted or I would be burning back ups and windows dir is empty

Any Hints?? By now when I search for "NTFS Raid" I find my own posts :lolflag:

Thanks
Richard

---

