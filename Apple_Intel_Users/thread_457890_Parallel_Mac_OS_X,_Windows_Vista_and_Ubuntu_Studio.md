---
title: "Parallel Mac OS X, Windows Vista and Ubuntu Studio with Boot Camp!?"
date: 2007-05-29
forum: Apple Intel Users
---

### Post by mac-user on 2007-05-29
Hi all,

I've an iMac, 20", 2x2.16 GHz, 1GB RAM, 256MB RAM in the graphic card with Mac OS X and Windows Vista installed.
Now I wish to install Ubuntu Studio, too, without having to reinstall on of the other systems, but _with_ repartioniring* the harddrive.
In the "[Macbook, Bootcamp, and ubuntu!]("http://ubuntuforums.org/showthread.php?t=457610")"-Thread I read, that's not as easy as it was on a normal PC - but is it possible?

I can't simple reinstall all, because this would mean, that I have to backup lots more than 100 GB of files oO

=/ i hope you have an idea!

micha


*Does this word exists? sorry, I'm german.

---

### Post by speedemonV12 on 2007-05-29
ia asked this same question over at the apple discussion forums... I have the same problem as you... i need a detailed tutorial on how to add a partition for  ubuntu (and do all the other stuff like bootloader and minor things)... while already having OS X and windows install via bootcamp... 

this is the response that i  got 



First, make a clone of your OSX partition.
Using iPartition reduce the size of the OSX partition while booted off the clone.
Now boot off the Ubuntu DVD & install in that recently freed space. Be very certain to install the boot loader to the same partition! (Last step of the install).

Before you delve into this, please spend time in the Ubuntu forums.

The first time I did this I hosed the WinXP partition by putting the boot loader on that partition.

Read, read, read - then do a fair amount of thinking! Backup your important data off WinXP & clone your OSX system.

And when choosing where to install Ubuntu, be absolutely certain you know what you are doing!

Good luck!

---

