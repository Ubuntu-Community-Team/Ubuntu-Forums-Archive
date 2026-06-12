---
title: "Accessing a vFAT partition I created"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-07-26
I created a 29.3GB vFAT partition out of some unformatted space on one of my drives.  The intention is to have some shared space between Ubuntu and Windows (I'm hoping to put my photos there).

Well, when I go to Places --> Computer and look at the drives that come up, I see my DVD-RW drive, 2 hard disk partitions showing their names (Shekky and Zippy), plus "File System" and the generically-named "29.3 GB Volume".

When I right-click and select "Mount Volume", it says it's unable to mount it, with the following details:

error: device /dev/hdb2 is not removable

error: could not execute pmount

When I type "mount" in a terminal (to show what's mounted where), I get:

/dev/hdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /tmp/disks-conf-hda1 type ntfs (rw)

So it's not showing "hdb2" as a drive that's already mounted (just wanted to check).

Any idea why I can't seem to make this happen?  I'd also love to be able to read from my main Windows NTFS volume, hda1.  It shows as "enabled" in Disks Manager, but have no clue how to read from it.

-Mark

---

### Post by mjpatey on 2006-07-26
By the way, in Disks Manager, when I try to "enable" my 29.3 GB vFAT partition, it does nothing.  Its status is "inaccessible" and hitting the enable button just refreshes the dialog box.

---

### Post by gurellia53 on 2006-11-10
_

---

### Post by gurellia53 on 2006-11-10
Ok, i'm a linux noob and i'm having the same problem. In the Disk Manager, i have my Windows XP ntfs partition, my vFat (FAT32) partition with some files that i want to share between OS's, my UBUNTU ext3  partition, and a swap partition. I've read that i can access the vFAT in linux but it won't let me enable it.

This is the only place i've found anything about the topic, so someone who knows what they're doing please help.

Thanx
  me

---

### Post by gurellia53 on 2006-11-10
oh great(sarcastically). i kno why. you can't mount extended partitions. i think.

darn

---

### Post by CatKiller on 2006-11-10
> **gurellia53 said:**
> This is the only place i've found anything about the topic

I don't think that's true: there must be a million links on this forum to these pages by now, but here's two more:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

> **gurellia53 said:**
> oh great(sarcastically). i kno why. you can't mount extended partitions. i think.

That's not exactly true, either. It's not so much that you can't mount an extended partition, as that there's no point. What you're after are the logical drives within the extended partition - they are what hold the data you want. The extended partition is just a box to keep the logical drives in.

---

### Post by gurellia53 on 2006-11-10
ok so i changed a few things. and those links above helped. in the terminal, i typed "sudo fdisk -l" and i found my vFAT was hda1.

so then i entered:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

and now it works

---

### Post by CatKiller on 2006-11-10
Excellent.

The /etc/fstab file is what controls disks being mounted automatically at boot up. You could edit that if you'd like that partition always mounted, or do it manually each time, as you choose.

Welcome to the community.

---

### Post by bodhi.zazen on 2006-11-10
> **CatKiller said:**
> Excellent.

The /etc/fstab file is what controls disks being mounted automatically at boot up. You could edit that if you'd like that partition always mounted, or do it manually each time, as you choose.

Welcome to the community.

How to edit fstab:

In a terminal type:```
sudo gedit /etc/fstab
```

Save and exit gedit.

Add the line:> /dev/hda1 /media/windows/ auto users,iocharset=utf8,umask=000 0 0

The partition will then mount at boot.

---

### Post by gurellia53 on 2006-11-10
Thanks a ton. i edited fstab and everything is working great.

Me = :D

---

