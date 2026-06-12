---
title: "backup Filesystem: raw copy/paste?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by daktari on 2007-02-07
Haven't found anything on this specific backup method in the forums:

Anything wrong with just copying _Filesystem_ to an external HD as a backup?

---

### Post by bodhi.zazen on 2007-02-07
What and how exactly are your trying to back up ? 

A single file or the entire OS ?

---

### Post by daktari on 2007-02-07
Intention is to save **"Filesystem" as is** - the whole thing (Dapper LTS): using "copy" and "paste" - literally.

From (source):
Places->Computer->Filesystem

To (target):
external HD->Filesystem

**"Filesystem"** contains **everything** I've got on the computer - the entire system menu tree resides there, other than CDRom and external devices.

File size is not an issue - under 10 GB

---

### Post by bodhi.zazen on 2007-02-07
Ah, you are looking to back up your partition ...

Well, you have several options.

**[color=red][http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7](http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7)**[/color]

If you use this copy method:

1. look at man cp

2. copy the data from a live CD with the partition mounted at say /media/ubuntu. If you copy the filesystem when it is mounted as your root partition I think you will copy some stuff in /dev /tmp and/or /var that may give you problems if you need to restore ;)

Partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

dd : [http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

---

### Post by daktari on 2007-02-07
Humble thanks - got it.

But I still have the same question - anything about the cut n paste method cause restore issues?  e.g., are the potential issues too varied and unpredictable to know what would happen on a restore attempt?

Brass tacks:

I have two identical laptops, one of which I hold in reserve.

If the laptop I use - or the LTS OS or the apps - goes tits-up for any reason, I'd like to have an external HD backup from which I can easily and simply replicate the entire OS and file system... if that clarifies anything worthwhile.

.

---

### Post by bodhi.zazen on 2007-02-07
> **daktari said:**
> Humble thanks - got it.

But I still have the same question - anything about the cut n paste method cause restore issues?  e.g., are the potential issues too varied and unpredictable to know what would happen on a restore attempt?

I wish I could be a little more informative on why as simple copy can be problematic, but I think it has to do with preserving permissions ...

Look at the first link I gave you and man cp for clues ..

> Brass tacks:

I have two identical laptops, one of which I hold in reserve.

If the laptop I use - or the LTS OS or the apps - goes tits-up for any reason, I'd like to have an external HD backup from which I can easily and simply replicate the entire OS and file system... if that clarifies anything worthwhile.

.

When it comes to backups I would steer you to tried and true methods :p

What do I do personally ?

I have  a /data partition and for my root partition I use gparted (the live gparted CD) that is to copy the partition.

Here is my feeble how to : [http://www.ubuntuforums.org/showthread.php?t=316237](http://www.ubuntuforums.org/showthread.php?t=316237)

Al least for me this is fast and reliable as long as you have the HD space.

You can also look at this : 

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

[http://www.ubuntuforums.org/showthread.php?t=240326](http://www.ubuntuforums.org/showthread.php?t=240326)

[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

[http://doc.gwos.org/index.php/Backup_restore_system](http://doc.gwos.org/index.php/Backup_restore_system)

Others prefer partimage.

After you look at all this, I would advise you perform and TEST a back up. For example I **know** I can restore my partitions with my backup method. That is the most important thing ...

---

### Post by dupa on 2007-02-07
> **daktari said:**
> Haven't found anything on this specific backup method in the forums:

Anything wrong with just copying _Filesystem_ to an external HD as a backup?


try to look over internet for "ghost 4 linux" -> g4l
maybe you can find it useful

---

### Post by daktari on 2007-02-08
Thanks for the steerage.

Separately:  One day, there will be a USB (or functionally identical) connection on every HD.  One day, there will be a GUI app that will allow you to connect two HDs and hard-copy the contents of one to the other.  One day...

---

### Post by dwblas on 2007-02-08
I have used tar for many years.  It keeps your directory structure intact, compresses, etc. and is extremely reliable.  See here for a rather lengthy discussion, which covers tar vs. copy.
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

