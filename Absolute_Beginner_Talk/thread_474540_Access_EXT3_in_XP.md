---
title: "Access EXT3 in XP"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-15
when i rarely use XP i want to access my EXT3.
i got a programme that allows me to see it in My Computer, but everytime i click it, it asks me if i would like to format?
that i dont want to do.
any ideas?

---

### Post by hyper_ch on 2007-06-15
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by 5-HT on 2007-06-15
I've had that problem in Ext2IFS, but it only happens infrequently and goes away after a reboot. Haven't really bothered to find out what's going on when it does occur. Perhaps looking at the projects homepage may provide some answers. 
Alternatively, if you only need read access you can use [explore2fs]("http://www.chrysocome.net/explore2fs")
cheers,

---

### Post by skymera on 2007-06-15
i got the program from fs-driver.org
the drive sows up in My Co mputer but i cant access it

---

### Post by ajgreeny on 2007-06-15
I agree with 5HT, get a copy of explore2fs for your windows installation and you can copy your files from ubuntu over to windows and work on them, save them to your windows partition and then later if needed, you can get them back to ubuntu by mounting the windows partition.  Works a dream, without any effect on either partition as you don't write to either one from the other, just copy files.

---

### Post by skymera on 2007-06-15
itsa nice thought.
but i would prefer read/write in windows.
thanks anyway

---

### Post by kfrance on 2007-06-15
I've been using Ext2IFS for a year and a half on two machines without a problem.  The only time I have a glich is if ubuntu crashes and the drives were not unmounted properly.  I then just have to boot into linux and shut down properly and then there are no problems.  See if that is your problem.

---

