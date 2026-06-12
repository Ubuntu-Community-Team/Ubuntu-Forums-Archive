---
title: "Use Breezy live CD to back up files to second drive?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by cbciv on 2006-06-04
All,

I have a Breezy installation that has developed missing inodes.  Before attempting to correct eveything, I'd like to back up a few files first (I was actually trying to figure out the best way to do regular backups when this occurred - a day late and a dollar short, I guess).

I can boot from a Breezy live CD and have partitioned and formatted the second drive (/hdc1) using gparted's live CD.  Now I'd like to 1) mount the primary drive (/hda1) read-only and 2) mount the second drive writable.  Then I'd like to either manually copy some files from /hda1 to /hdc1 (more than will fit on a floppy) or better yet use dump or something to backup as much of /hda1 as is readable.

Questions:

1. Am I doing things the hard way?  Is there something better that I don't know about?

2. If this is a good approach, how do I create a mount point and mount /hdc1?  The examples that I found seems to include creating a directory on /hda1 and mounting the other drive to it, but obviously I can't do that on a drive mounted read-only.

I'm happy to get pointers to how-tos, man pages, etc.  Thanks!

---

### Post by nanotube on 2006-06-04
[QUOTE=cbciv]All,

I have a Breezy installation that has developed missing inodes.  Before attempting to correct eveything, I'd like to back up a few files first (I was actually trying to figure out the best way to do regular backups when this occurred - a day late and a dollar short, I guess).

I can boot from a Breezy live CD and have partitioned and formatted the second drive (/hdc1) using gparted's live CD.  Now I'd like to 1) mount the primary drive (/hda1) read-only and 2) mount the second drive writable.  Then I'd like to either manually copy some files from /hda1 to /hdc1 (more than will fit on a floppy) or better yet use dump or something to backup as much of /hda1 as is readable.

Questions:

1. Am I doing things the hard way?  Is there something better that I don't know about?

2. If this is a good approach, how do I create a mount point and mount /hdc1?  The examples that I found seems to include creating a directory on /hda1 and mounting the other drive to it, but obviously I can't do that on a drive mounted read-only.

I'm happy to get pointers to how-tos, man pages, etc.  Thanks![/QUOTE]
when you boot to livecd, your / is a ram drive, not a real hd. so you can mount both your hda1 and your hdc1 to somewhere it your filesystem, one read-only, one rw, and make the copy.
so you wouldnt be creating a directory on your hda1, you would be creating a directory in your ram-/, and then mounting hda1 to it. 

and yes, it seems like a good process for backing stuff up out of your messed up drive. 

first, i'd make sure to back up the "important" dirs, and then if that works, you can try to be daring and do the whole thing, with something like "cp -r /mnt/hda1/* /mnt/hdc1/backup/"

---

### Post by aysiu on 2006-06-04
What are missing inodes? They can't be fixed?

**Ubuntu live CD**: ```
sudo mkdir /recovery
sudo mkdir /old
sudo mount -t ext3 /dev/hdc1 /recovery
sudo mount -t ext3 /dev/hda1 /old
gksudo nautilus
```

**Kubuntu live CD**: ```
sudo mkdir /recovery
sudo mkdir /old
sudo mount -t ext3 /dev/hdc1 /recovery
sudo mount -t ext3 /dev/hda1 /old
kdesu konqueror
```

Then copy away!

---

### Post by AndyCooll on 2006-06-04
You mount your drives by creating mount points by typing the following into a command line as follows:

```
sudo mkdir /media/hda1
```

And then:

```
sudo mount -t ext3 /dev/hda1 /media/hda1
```

:cool:

---

### Post by cbciv on 2006-06-09
Thanks!  Your suggestions got me up and running.  I've successfully backed up the files and will move on to running fsck and attempting to repair the errors.

Charles

---

