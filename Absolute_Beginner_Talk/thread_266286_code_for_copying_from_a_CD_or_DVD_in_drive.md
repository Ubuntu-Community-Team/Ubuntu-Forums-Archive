---
title: "code for copying from a CD or DVD in drive"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-09-27
Using Ubuntu 6.06lts
1.  Could someone please advise the terminal code to copy data from either a DVD or a CD in a drive to a partition on a hard disk. My drives show as 1. DVD RW /dev/hda and 2. CD RW /dev/hdb  under System>Admin>Disks. 
(Should the cd drives be mounted if using SystemRescueCD to copy data from a drive to partition)

2. Should DVD and CD drives be permanently mounted and  dir made or just when there is a disk in drive? If so how should mount and make dir, they currently appear as cdrom and cdrom0 under /media but the CD RW drive also comes up as /media/cdrecorder if a disk is placed in the drive. I have NeroLINUX which states on startup that it cannot access /dev/sd0 and /dev/sg1 whatever they represent?

3. Could someone knowledgable please check this mount printout and advise what mistakes I have made in mounting etc:-

root@jeff123-Main:/# mount
/dev/sdb8 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda5 on /media/sda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda6 on /media/sda6 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda7 on /media/sda7 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb5 on /media/sdb5 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb7 on /media/sdb7 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb5 on /media/SpareDrive type vfat (rw,iocharset=utf8,umask=000)
/dev/sdb6 on /media/WinSpare type vfat (rw,iocharset=utf8,umask=000)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=jeff123)
/dev/hdb on /media/cdrecorder type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8)

sdb8 is my ubuntu partition and it appears I have botched it somehow. 

4. How can I have mount display the revelant partitions by the allotted names such as sdb5 is 'SpareDrive' and sdb6 is 'WinSpare' etc but the windows partitions (and Ubuntu sdb8) although ahowing as icons on the ubuntu desktop dont show by name as do the vfat32 data drives I have set up.

Apologies for the long post, Even though everything works fine and I am rapt in Ubuntu and Linux generally I am still stumbling around trying to get a grasp after windows and would like to set up with correct procedures and methods. Any assistance appreciated.

---

### Post by Bachstelze on 2006-09-27
1) the cp and mv commands are your friends, the manual for them explains it all :) And yes, the CD must be mounted. By definition, the data on an unmounted drive cannot be accessed.

2) If there is no disk in a drive, by definition you cannot mount it. NeroLINUX stinks, by the way, get k3b :)

3) No problem here.

4) You just have to change the mountpoint. Edit your /etc/fstab file, go to the line regarding the partiton you want to change the mountpoint for, and change /media/sd** to /media/whateveryouwant, then reboot to apply changes. Maje sure you have created the directory for the new mountpoint beforehand.

---

### Post by Gerry Atric on 2006-09-27
Many thanks advice much appreciated.

---

