---
title: "EXT3 partiton resize"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by saadakhtar on 2007-01-06
**is there any way to resize my ext3 partition?**
i repartitioned my **60 gig hdd** on my laptop and made **10 gig free space for ubuntu** when i first started off.
now that i am well aquainted with ubuntu and hardly ever use win-xp **(i am dual booting)** i wish to completely remove my win-xp installation and add that disk space for my ext3 partition that is holding m ubuntu installation.

I could just backup all my data on ubuntu and format the whole drive but i need to know if i can achieve this task  without wiping off everything.

The WIN32 compatible application for doing such a task for windows compatible drives is Partition Magic. Could anyone guide me to a similar software for ubuntu or give me a basic outline of what i will need to do.

thanks

---

### Post by CroEragon on 2007-01-06
Thats something i wanted to ask somebody with more knowledge.
Ext3 writes files so if you spend 30% of drive, one big file could be at he end of drive. Doesn't it make Ext3 impossible to resize without wiping it?

---

### Post by saadakhtar on 2007-01-06
i just installed Gparted. it seems to allow me to resize any windows compatible partitions but ext3 partiton seems to be locked for any action. As far as my common sense tells me. i suppose if the ubuntu partition was not locked then i could just format the ntfs partition that is holding my other os to ext3 and then just add that free space to the main ext3 partition that i holding my ubuntu installation.

anyone has any ideas about this. or is there any other way to do this.

---

### Post by jglitch on 2007-01-06
That is exactly one of my problems. we need an experienced tux to help us. good thread.

---

### Post by UltraMathMan on 2007-01-07
You cannot resize the ext 3 partition because it is mounted and in use by the system. However booting from a Live CD and running GParted there should allow you to resize the ext 3 partition.

Check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=328677&highlight=resize+ext3+partition")

---

### Post by housam on 2007-01-07
You can download Gparted (through ubuntu)and burn it to have the bootable (live)CD. then boot from the CD and you can format or resize whatever you want.

---

### Post by meng on 2007-01-07
I believe the latest GParted LiveCD has the best support for resizing AND moving ext3 partitions.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by STREETURCHINE on 2007-01-07
yes i have gparted on disk and it is good ,you can resize your partition but backup the important stuff first.
  just in case (it has never destroyed any of my info but )

---

### Post by meng on 2007-01-07
Ditto, backup in case of unexpected disaster.

---

### Post by saadakhtar on 2007-01-08
wow Gparted live cd worked like a charm. Finally i am free from MS. this is just so much better.
Thanks

---

