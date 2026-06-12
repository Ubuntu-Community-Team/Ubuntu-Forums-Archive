---
title: "[SOLVED] New hard drive.  How to partition so ubuntu can see it?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-20
New hard drive.  How to partition so ubuntu can see it?

---

### Post by Inxsible on 2007-11-20
you can partition it anyway you like actually. If you mean what file system to use, then it depends on what you plan to use the drive for.

if you use the drive mostly with Windows, then use the NTFS filesystem. If you use the drive with Ubuntu more, then use EXT3.

Ubuntu can read and write to NTFS(since Gutsy) and FAT32 systems. Windows can see the EXT2/EXT3 partitions once you install the fs-driver

---

### Post by Tdukes on 2007-11-20
> **Inxsible said:**
> you can partition it anyway you like actually. If you mean what file system to use, then it depends on what you plan to use the drive for.

if you use the drive mostly with Windows, then use the NTFS filesystem. If you use the drive with Ubuntu more, then use EXT3

I have it set to ext3 using GParted.  It wont show up though

---

### Post by Inxsible on 2007-11-20
> **Tdukes said:**
> I have it set to ext3 using GParted.  It wont show up thoughSince this is a different drive, have you clicked the drop down on the top right corner to select the other drive?

Only 1 drive is shown at a time in GParted.

---

### Post by Tdukes on 2007-11-20
> **Inxsible said:**
> Since this is a different drive, have you clicked the drop down on the top right corner to select the other drive?

Only 1 drive is shown at a time in GParted.

yes.  I selected the drive and partitioned it.  It says its unmounted though,  am I supposed to flag it or something?

[IMG]http://img.photobucket.com/albums/v618/Tommydukes/Screenshot--dev-sdb-GParted-1.png[/IMG]

---

### Post by bodhi.zazen on 2007-11-20
You will have to add it to /etc/fsab

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

> /dev/sdb1 /media/<name> ext3 auto,users,rw 0 2

Then :

```
sudo mkdir /media/<name>
sudo mount -a
```

Change <name> to the name you want to give the mount point, like say

/media/music or /media/data or ...

---

### Post by Inxsible on 2007-11-20
you cannot mount the drives using GParted. to mount the drive you need to use the mount command
```
sudo mkdir /media/sdb
```then ```
sudo mount /dev/sdb /media/sdb
```

---

### Post by Tdukes on 2007-11-20
> **bodhi.zazen said:**
> You will have to add it to /etc/fsab

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)



Then :

```
sudo mkdir /media/<name>
sudo mount -a
```

Change <name> to the name you want to give the mount point, like say

/media/music or /media/data or ...

You are the best.  thanks man

---

