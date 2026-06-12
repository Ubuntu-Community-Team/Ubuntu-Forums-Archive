---
title: "Mounting a new HD"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by murmsk on 2006-11-30
I am trying to install a new hard drive.
I have it formated ok ,I think ,but can't seem to mount it or create a mount point.  Where should I look for help? I am using edgy.

thanks  steve

---

### Post by taurus on 2006-11-30
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by zgornel on 2006-11-30
Gparted should give you the information you need about the partition names. For example, if your hdd is /dev/hdb, go to :/dev/disks/by-uuid and do a *ls -l* to see which uuid points at /dev/hdbX (where /dev/hdbX (is) are the partitions on /dev/hdb). Edit your /etc/fstab accordingly (*man fstab* for more info) and then do *mount /dev/hdbX*

EDIT: Use the links provided by taurus :D

---

### Post by rbprogrammer on 2006-11-30
i'm not familiar with ubuntu, but if you are using kubuntu, try going to [ K Menu -> System Settings -> Advanced -> Disk and Filesystems] .  see what you can do from there.  if the drive is detected, just create a new mount point.  

if its not detected, i dont know what to say but maybe check your master and slave jumpers on the drives are set correctly.

---

### Post by bodhi.zazen on 2006-11-30
> **murmsk said:**
> I am trying to install a new hard drive.
I have it formated ok ,I think ,but can't seem to mount it or create a mount point.  Where should I look for help? I am using edgy.

thanks  steve

I assume you new HD is /dev/hdb

```
sudo mkdir /mnt/hd
sudo mount /dev/hdb1 /mnt/hd
```

You can call the mountpoint, "hd" any name you like and you can put it in /mnt or /media, or actually anywhere you like....

Your fstab entry and management of permissions depends on what file system you have on the HD, vfat, ntfs, or linux (ext3, reiser, jfs, ....)

In gerneral:```
sudo gedit /etc/fstab
```

Add an enty like this:> /dev/hdb1 /mnt/hd auto auto,users,<other_option_here> 0 0

---

### Post by cytutchi on 2006-11-30
hey people...
ok worked for me...mounted it!
but now i need also to get access...
let me give you some specific info...

the hard disk is called:hda2

....the mount point i used is at:
/home/cytutchi/Desktop/windows

in the fstab file i wrote:
/dev/hda2	/home/cytutchi/Desktop/windows	ntfs	defaults,utf8,umask=007,gid=46 0       1

...can somebody tell me now how can i gain access so i can copy/exectute/....???
thenx a lot people!!

---

### Post by taurus on 2006-11-30
If you want to write to ntfs filesystem, you need to install ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by CatKiller on 2006-11-30
> **bodhi.zazen said:**
> In gerneral:```
sudo gedit /etc/fstab
```

Tut, tut ;)

```
**gk**sudo gedit /etc/fstab
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by bodhi.zazen on 2006-11-30
> **CatKiller said:**
> Tut, tut ;)

```
**gk**sudo gedit /etc/fstab
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

LOL :lol: Thanks CatKiller ;)

---

### Post by cytutchi on 2006-11-30
just replyin to say that thought of another way to cheat as well for the system...
instead of installing the ntfs suport for dapper...
i copy out from that hard disk(windows installed there) n just use it as i want or i save it in a common space that i have and if i log on again to windows i take it from there...
but if just needed for playing or using easy to do since caffeine can play the videos or amarok the mp3s as they are!

chiers people!

---

