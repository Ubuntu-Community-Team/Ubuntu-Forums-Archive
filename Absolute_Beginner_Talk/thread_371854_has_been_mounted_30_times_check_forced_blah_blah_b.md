---
title: "has been mounted 30 times check forced blah blah blah"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-02-27
Anyway to stop it from checking for errors every thirty times?  It is rather annoying when I need to do something quickly because I have to go.

---

### Post by christhemonkey on 2007-02-27
See this thread:
[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

---

### Post by kinematic on 2007-02-27
sudo tune2fs -c 0 /dev/hda#
you can use the -c switch to set the number of bootups before the check is forced....zero in this case means disabled.

edit:seems to me bonager is just a frontend to tune2fs.

---

### Post by g3k0 on 2007-02-28
zaccheus@geckoLaptop:~$ sudo tune2fs -c 0 /dev/hda
tune2fs 1.39 (29-May-2006)
tune2fs: No such file or directory while trying to open /dev/hda
Couldn't find valid filesystem superblock.
zaccheus@geckoLaptop:~$

---

### Post by bodhi.zazen on 2007-02-28
You haev to give a partition number, something like /dev/hda**1**

Give the partition you do not want checked ...

To list your partitions : ```
sudo fdisk -l
```

---

### Post by PureW on 2008-01-23
I have this problem too, with the disks being scanned. 
Is this a problem for everyone using linux? Or is something wrong with my system?

This is my /var/log/fsck/checkfs:
> $ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a 
Wed Jan 23 17:38:47 2008

fsck 1.40.2 (12-Jul-2007)
Replaying journal..
/dev/sdb2: clean, 139267/854784 files, 933480/1708914 blocks
Reiserfs journal '/dev/sda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x803 of format 3.6 with standard journal
Blocks (total/free): 24414768/19489084 by 4096 bytes
Filesystem is clean
/dev/sda4 has been mounted 22 times without being checked, check forced.
Reiserfs super block in block 16 on 0x803 of format 3.6 with standard journal
Blocks (total/free): 24414768/19489084 by 4096 bytes
Filesystem is clean
/dev/sda4: 2559/43958272 files (43.8% non-contiguous), 33114478/87915712 blocks

Wed Jan 23 17:44:44 2008
----------------
$ 

---

### Post by SunnyRabbiera on 2008-01-23
No there is nothing the matter here, its supposed to do this

---

### Post by jd65pl on 2008-01-23
> **PureW said:**
> I have this problem too, with the disks being scanned. 
Is this a problem for everyone using linux? Or is something wrong with my system?

This is my /var/log/fsck/checkfs:

Its not so much as a problem as a feature. Checking the hard drive for consistency and there are no impending errors

---

### Post by DarkDancer on 2008-01-23
It's not a problem, it's supposed to do that, but you can turn it off if you want.

---

### Post by SunnyRabbiera on 2008-01-23
> **jd65pl said:**
> Its not so much as a problem as a feature. Checking the hard drive for consistency and there are no impending errors

Just be careful with how you phrase that, remember microsoft once said that the blue screens it has are not a flaw but a feature...

---

### Post by mivo on 2008-01-23
Yep, it is doing that to prevent any possible, small errors from turning into large catastrophies. I'd not disable this (one of the above posts explains how though, if you want to do it), because it's just part of the system maintenance. Like I said, it's easier to fix problems when they are small, and much harder to counter them when they have become huge.

---

### Post by kaboodle_fish on 2008-01-23
I use AutoFsck which allows you to set the checking to be carried out on shutdown and how often

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by sports fan Matt on 2008-01-23
Like mivo and others have said, its checking the discs and im not sure about you, but I would rather take the extra time to check them then have castrophies later compromising  a possibly hosed system..just my .02

---

### Post by Sidewinder1 on 2008-01-23
Never, never run fsck on a mounted drive / file-system!

---

### Post by stchman on 2008-01-23
> **g3k0 said:**
> Anyway to stop it from checking for errors every thirty times?  It is rather annoying when I need to do something quickly because I have to go.

Not a good idea to disable this feature.  This keeps your filesystem healthy.  You might be able to delay it to 50 or so but I would not disable this feature.  30 times translates to about once a month for the average user.

If you don't put EVERY single file on your / partition then the fsck is actually fairly quick (approx 2mins).

---

### Post by leader303 on 2008-02-24
good idea or not... i want to uninstall bonager, but:

```
Removing bonager ...
update-rc.d: /etc/init.d/bonager exists during rc.d purge (use -f to force)
dpkg: error processing bonager (--remove):
 subprocess pre-removal script returned error exit status 1
 System startup links for /etc/init.d/bonager already exist.
Errors were encountered while processing:
 bonager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what to do?

---

### Post by Martje_001 on 2008-02-24
You have to remove the bonager startup scripts, I think..

---

