---
title: "Mount D: as home"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Lord DarkPat on 2008-01-16
Is it possible for me to mount my windows D: drive as /home, without losing the files?
I'm on the xubuntu livecd right now(it takes ages to bring up the partitioner, been waiting for 10 mins)

---

### Post by Nolander on 2008-01-16
do u mean mounting it to /home/$USER? if so i thing i should be all right aslong as there is no other file in that dir. but u will need to install [ntfs-g3]("http://ubuntuforums.org/showthread.php?t=217009").

-nolander

---

### Post by nille on 2008-01-16
I recently found someone else who tried that, and it didn't go too well, so I wouldn't recommend it. But there are other ways to make the files available in your home-directory. I'll assume your "D:" is in /etc/fstab, and is now mounted as /media/d-drive, then you could follow **one** of these two instructions (preferrably the first):

**Option 1:** Create a link to your partition, so that the partition is directly accessible in your home-directory:
```
ln -s /media/d-drive /home/username/d-drive
```


**Option 2:** Change the mountpoint of your partition, so that it gets mounted somewhere inside your home-directory.

Create the new mountpoint:
```
mkdir /home/username/d-drive
```

Then make the appropriate changes in your /etc/fstab file. That is, change /media/d-drive into /home/username/d-drive and save.
```
gksudo gedit /etc/fstab
```

Reboot.

---

### Post by Lord DarkPat on 2008-01-16
it's not mounting on the livecd. It's supposed to be /media/sda5

---

### Post by nille on 2008-01-16
Oh, I missed that you are using the LiveCD..

My advice is that you install either using a separate /home-partition, or by letting it be part of the /-partition. And then you could either mount your sda5 as /home/username/sda5 (Option 2), which is an alternative during installation, or you could choose the mountpoint to be /media/sda5 (or perhaps /mnt/sda5) and after installation make a link, as described above (Option 1).

---

