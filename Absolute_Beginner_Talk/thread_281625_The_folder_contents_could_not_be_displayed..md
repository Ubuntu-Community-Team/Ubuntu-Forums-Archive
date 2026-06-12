---
title: "The folder contents could not be displayed."
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by bazmond on 2006-10-21
[CENTER]"The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "windows"."
[/CENTER]

I'm new to Ubuntu so please excuse any technical inaccuracy's. I have a second ATA hard drive that i have stored all of my media on, it uses an NTFS. I'm having a hard time accessing the drives content. Every time i try to access the 'Second Disk'  from 'Computer' or through '/media/windows' i get the above error.My friend helped me out and got me to try the following through Terminal. 


$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-amd64-generic/volatile type tmpfs (rw)
/dev/hdb1 on /tmp/disks-conf-hdb1 type ntfs (rw)

$ ls /tmp/disks-conf-hdb1
ls: /tmp/disks-conf-hdb1: Permission denied
$ sudo umount /tmp/disks-conf-hdb1
Password:

$ sudo mkdir /media/windows
$ sudo mount /dev/hdb1 /media/windows
$ sudo umount /media/windows
$ sudo mount -o umask=007 /dev/hdb1 /media/windows


Unfortunately we were unsuccessful and still cannot access the content of the drive, however i can list the content of specific folders through the Terminal using...

$ sudo ls /media/windows/Shared\ Documents/Albums

Any help would be most appreciated, thanks for your time.

---

### Post by Bartender on 2006-10-21
Could you post the results of

sudo cat /etc/fstab

---

### Post by maaronB on 2006-10-21
Read and follow:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Bartender on 2006-10-21
maaron -
aysiu's directions mention making a backup of fstab

sudo cp /etc/fstab

Where does this backup go?  How does one access it?

---

### Post by bazmond on 2006-10-21
> **Bartender said:**
> Could you post the results of

sudo cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks for the quick responses :D

---

### Post by maaronB on 2006-10-21
I am no expert, I just had a similar problem before and the guide helped me.

So I am probably wrong but I believe that this command makes the backup.

sudo cp /etc/fstab /etc/fstab_backup

all this does is create a new file named fstab_backup exactly like the current fstab.

Then if you screw up fstab all you have to do is delete the one you screwed up and rename /etc/fstab_backup to /etc/fstab

The backup would normally just stay in the /etc/ directory and just change it's name to use it.

---

### Post by Bartender on 2006-10-21
Yeah, if your fstab folder doesn't include the proper entry for your Windows hard drive Ubuntu won't access it automatically.  That's probly not a technically accurate way of saying it, but from one newb to another it's close enuf ;) 
Aysiu has spent a lot of time and effort writing up guides for the most common challenges.  See if you can follow his guide.

---

### Post by bazmond on 2006-10-21
Bartender and maaronB i thank you both, i will report my success after following the guides.

Bazmond.

---

### Post by Bartender on 2006-10-21
Here's another [guide]("https://help.ubuntu.com/community/MountingWindowsPartitions") that covers the issue, from Ubuntu Document [Storage]("https://help.ubuntu.com/community/")

Sometimes it helps to read a few different guides on the same subject.

When you aren't faced with an immediate crisis, it'd be good to browse thru the Document Storage website and just get a feel for what's there.

---

### Post by bazmond on 2006-10-21
SUCCESS Aysiu guide worked, had to add another line to fstab using nano, anyhow i will continue to read on, i thank u again.

---

