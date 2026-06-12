---
title: "external fat32 drive problem"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by ohmyiv on 2006-08-03
Hi,

I'm new to Ubuntu (and linux in general), and I'm having issues with my external drive.  I have a 250G Lacie external drive, formatted as fat32.  My problem is, I can't write to it, or change any data on it. I already tried changing the permissions by right clicking on the drive and using the properties interface an it won't work.  I'm hoping someone can help me out, it's so frustrating.   

Thanks in advance to anyone who can help.

---

### Post by annda on 2006-08-03
hi,

what do you mean exactly that it didn't work? have the permissions changed and you still can't to the drive? or did changing the permissions fail?

what exactly are the permissions and who is the owner of the drive?

---

### Post by ohmyiv on 2006-08-03
thanks for the quick reply.  according to properties, the owner can view and modify content, and the owner is user:mitch (me), but i still can't write to the disk or modify the data. i can provide you with any other info, if needed.

---

### Post by annda on 2006-08-03
what info do you get about your drive when you type
```
mount
```
in the terminal?

specifically, what is the value of umask?

---

### Post by ohmyiv on 2006-08-03
hi, i had to reinstall dapper, so i'm starting with a fresh installation now

mount=

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sda1 on /media/LACIE type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1 000,gid=1000,umask=077,iocharset=utf8)
```

---

### Post by pomegranate on 2006-08-03
I'm also having this problem, have done the same permission changing as the OP. Doing mount gets me:
> tom@ubuntu:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw)
/dev/sda2 on /media/usbdisk type ext3 (rw,noexec,nosuid,nodev)
/dev/sda1 on /windows type vfat (rw)


The disk I'm trying to write to is the last one, sda1. That and sda2 are two partitions on the same physical, external disk. Can't see anything to do with umask. What does it mean, out of curiosity?

---

### Post by anaconda on 2006-08-03
have you tried to write to your disk with root rights.. should work.

type to terminal:

gksudo nautilus

or

sudo su

and then try to write to your external disk..

---

### Post by gilgongo on 2006-08-03
> **anaconda said:**
> have you tried to write to your disk with root rights.. should work.

type to terminal:

gksudo nautilus

or

sudo su

and then try to write to your external disk..

If that works, it'll mean you'll always have to access that drive as root. This surely isn't a very good solution is it?

Mounting drives (both fixed and removable) read-only is in my opinion the biggest single problem with Ubuntu. Why on earth (apart from NTFS drives, obvioulsy) should a desktop OS want to prevent you from writing to your own drives?

And if anyone comes out and says something smug about "security" - I have a clue-by-four I'd like to slap them with.

---

### Post by pomegranate on 2006-08-03
> **anaconda said:**
> have you tried to write to your disk with root rights.. should work.

type to terminal:

gksudo nautilus

or

sudo su

and then try to write to your external disk..

Well, that worked, thanks a lot. But is there anyway I can set things up (simply, I'm new to all this) so that I won't have to do that every time I switch on my external drive? Like a permanent setting? Additionally, can you help me with something similar: Everytime I restart Ubuntu, I have to type sudo mount-a to be able to access the fat32 partition of my external disk - I can access the ext partition on the disk without doing that. I'd prefer not to have to do that everytime either. I don't understand quite why I have to it everytime...

---

### Post by annda on 2006-08-03
sorry, my bad. i suggested to look for things that are important for non-removable disks, with which i used to have a similar problem (and they can be solved by editing entries in /etc/fstab but it doesn't apply to dynamically mounted removable disks). i was able to fix my permissions problem with changing umask=00 to umask=000 (umask displays/sets permissions for disks/partitions).

however, it seems not to work with removable drives, as they are not normally included in /etc/fstab.

sorry, i can't help you any further. i don't see much difference with your configuration and mine:

```
/dev/hda8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw)
/dev/hda5 on /media/hda5 type vfat (rw)
/dev/hda6 on /media/hda6 type vfat (rw,umask=000)
/dev/sdb1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=106,umask=077,iocharset=utf8)
/dev/sdc1 on /media/Archiwum type ntfs (rw,nosuid,nodev,uid=1000,gid=106,umask=077,iocharset=utf8)
/dev/sdd1 on /media/GMINI402 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=106,umask=077,iocharset=utf8)
```

i can write to all my vfat drives. i hope someone can spot the difference and point you to the right direction...

---

### Post by ohmyiv on 2006-08-03
thanks for all the help.  i logged in as root and i was able to do what i wanted with my external drive.  i was really hoping i could do those things with my regular login.  if anyone knows how, that would be wonderful

---

### Post by mc^2 on 2006-08-24
add yourself to group disk (i think it's nr 6) in /etc/group. Then set umask=007,gid=6 in mount options in /etc/fstab. That should do the trick. I did it this way on my debian before switching to ubuntu. It seems that ubuntu uses gid=46 to do the same.

---

### Post by Frank Golden on 2006-08-24
> **ohmyiv said:**
> Hi,

I'm new to Ubuntu (and linux in general), and I'm having issues with my external drive.  I have a 250G Lacie external drive, formatted as fat32.  My problem is, I can't write to it, or change any data on it. I already tried changing the permissions by right clicking on the drive and using the properties interface an it won't work.  I'm hoping someone can help me out, it's so frustrating.   

Thanks in advance to anyone who can help.
What is the output of sudo gedit /etc/fstab

---

