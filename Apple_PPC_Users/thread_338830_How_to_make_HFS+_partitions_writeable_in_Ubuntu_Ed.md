---
title: "How to make HFS+ partitions writeable in Ubuntu Edgy?"
date: 2007-01-15
forum: Apple PPC Users
---

### Post by mystlynx on 2007-01-15
Hi guys.

I have installed Mac OS X 10.4.8 and Ubuntu Edgy 6.10 as dual boot in my mac.

I want to make HFS+ partitions writeable in Ubuntu, but I can't get success.

I try to mount HFS+ partition as writeable by use this command:

mount -w -t hfsplus /dev/hda2 /media/mac

Then i try to write a file to HFS+ partition:

cd /media/mac
touch test.txt
touch: can not touch ‘test.txt’: Read-only file system

after, i installed a packages that named 'hfsplus' and try to mount HFS+ partition by use 'hpmount' command:

hpmount /dev/hda2 /media/mac
hpmount: /dev/hda2: This is not a HFS+ volume (Unknown error 4294967295)

Anyone tell me what problem?

My kernel version is 2.6.17-10-generic #2 SMP

Am i need upgrade my kernel by manual?

---

### Post by fkdev on 2007-01-15
You need to disable journaling. There is no way to write to a journaled HFS+ partition, right now.

From the Mac OS command line

```
 sudo diskutil disableJournal Macintosh\ HD/ 
```

(Shamefully copied from this thread: [http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960))

---

### Post by saserlite on 2007-07-08
Once you have configured your disk to be HFS+ with journalling disabled, you may need to take ownership of the disk to regain control from within Ubuntu.

```
sudo chown yourusername disktotakeownershipof
```

Once you have run that command, if you already have the disk visible within a Nautilus window, you will have to refresh it (F5) to view the changes.

---

