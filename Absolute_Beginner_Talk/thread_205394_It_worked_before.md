---
title: "It worked before?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-06-28
Hi everyone,

Until recently I had Breezey Badger installed on my system for several months and apart from a few odd problems everything worked rather well.  Anyway, I have just updated to Dapper and now I cannot get access to my USB hard-drive (see screenshot).  I followed some instructions for mounting HDD, but got absolutely nowhere.  Is there any easy answer to this problem?

In fact, my HP psc2410 all-in-one printer doesn't work either.  I thought Dapper was supposed to be an improvement over Breezey?  Other than these minor irritating problems, I look forward to unplugging XP for the very last time.

Thank you for any answers in advance.


Regards


Mark     :confused:

---

### Post by Keith_Beef on 2006-06-28
The warning says that only root can mount the device. Have you tried the following?

```
sudo mount /media/sda6
```

If this works, then you might need to edit your /etc/fstab file, to allow normal users to mount the filesystem.

Beef.

---

### Post by Norfolk 'n' Good on 2006-06-28
Thanks Beef that did the job nicely.  After all that the solution was relatively simple!:D

---

