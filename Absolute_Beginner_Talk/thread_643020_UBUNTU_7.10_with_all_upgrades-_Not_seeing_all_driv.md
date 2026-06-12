---
title: "UBUNTU 7.10 with all upgrades- Not seeing all drives"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by ghoran on 2007-12-17
I installed 7.10 on two desktops.
Each desktop has extra hard drives.
They are all IDE

Computer 1: Has a main drive, two extra hard drives, a floppy drive and a cdrom drive.
I see the main drive, one extra hard drive, a floppy drive and cdrom drive.
I am missing a hard drive.

Computer 2 has a main drive, an extra hard drive, a floppy and a cdrom drive. On the second computer I see.
The main drive, cdrom drive and floppy.
I am missing a hard drive.
In addition it sees the one hard drive as a SCSI.
/dev/sda1   <- Why does it see this drive as a scsi?
and it does not see the other drive?

I believe that the live cd saw these other drives. I don't remember now :) I guess I could boot off the CD if I need to.

Here is a dump of the /etc/fstab files from the computers

Computer 1:

gary@gary-desktop:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dca5e02e-241e-411b-88a4-eda8f151d10f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5d381af8-0fd0-48d8-9d33-a8aaafc40119 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
gary@gary-desktop:/etc$


Computer2:
ash@ash-desktop:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d86f6a20-e6f5-4d4a-91d6-1f815d5f0fba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e44b69fc-2818-496f-b461-f3c0d0a88413 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
ash@ash-desktop:/etc$


Here is the command line display of the drives
Computer 1:
gary@gary-desktop:/etc$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             11851452   2345632   8903788  21% /
varrun                  127968        88    127880   1% /var/run
varlock                 127968         0    127968   0% /var/lock
udev                    127968        84    127884   1% /dev
devshm                  127968         0    127968   0% /dev/shm
tmpfs                   127968     34696     93272  28% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc1              1584320   1185408    398912  75% /media/disk
gary@gary-desktop:/etc$


Computer 2:
ash@ash-desktop:/etc$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              5874396   2307920   3268072  42% /
varrun                  127968        84    127884   1% /var/run
varlock                 127968         0    127968   0% /var/lock
udev                    127968        52    127916   1% /dev
devshm                  127968         0    127968   0% /dev/shm
lrm                     127968     34696     93272  28% /lib/modules/2.6.22-14-generic/volatile
ash@ash-desktop:/etc$

Thanks for your help.


Also could a moderator tell me if I should be in a different forum (Installation and Upgrades) instead of beginner talk.
I feel I am a beginner and did not want to assume I should move over :)

---

### Post by brunetteredhead on 2007-12-17
I didn't really have time to look into your config in great detail, but I noticed that only two of your hard drives on computer 1 were listed in the fstab file.  This means that one of the hard drives is not set to automatically mount.  You should issue a "mount" command on each of the computers to see which of the drives are available to mount.  If you see a drive listed in the results of the mount command but that drive isn't in your fstab, then all you will have to do is add the drive that needs to be mounted into the fstab with the proper flags.  Issue the mount command and I may be able to look into your problem a little bit further.

Thanks.

---

