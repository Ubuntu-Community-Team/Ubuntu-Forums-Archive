---
title: "Partitioning length?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Speediakal on 2006-11-13
How long should it take to partition my drive? i put up like 16% (29.9GB) and its been up for like 10 minutes and it hasn't gone to step 6. or should this be taking like a whole hour or something?

---

### Post by smoker on 2006-11-13
depends what you are doing, and also how big the drive is. if you are resizing an existing partition it will take longer as the app has to move data to make space for the new partition

---

### Post by Speediakal on 2006-11-13
like how long? i tried puttin up 1%(1.2GB) and i had it up for like 15 minutes, then just gave up. I have XP installed also. should i defrag the disk?

---

### Post by smoker on 2006-11-13
hi, if you have xp installed and you are making a new partition for linux, then you should definately defrag, i would give the xp system a good clean up, ie, get rid of all unused apps, temp files, old restore points, then defrag and backup before repartitioning.

if you are finding trouble running the partitioner, try running chkdsk on xp in case there is a fault in the harddrive.

---

### Post by CatKiller on 2006-11-13
> **Speediakal said:**
> like how long? i tried puttin up 1%(1.2GB) and i had it up for like 15 minutes, then just gave up. I have XP installed also. should i defrag the disk?

I'm not entirely sure what you mean by "putting up", but it's possible that you are telling the installer to resize your existing XP partition to 1% of its existing size. This might well take a while, especially if the partition is heavily fragmented.

You should definitely defragment a partition before you attempt to resize it. That will limit the number of file fragments that need to be moved around during the resize process. The good news is that when you replace that space with a sensible Linux filesystem, you won't need to defragment your files. Pretty much ever.

---

### Post by Speediakal on 2006-11-13
how can run a chkdsk or defrag without going into my account? like during a boot or something?

---

### Post by smoker on 2006-11-13
hi, to run a chkdsk on winxp, click start, run, and type cmd, on the screen that opens up, type 'chkdsk /r /f' without the quotes and a space before each / this is if your xp is on c:\ drive. it will ask you to allow the chkdsk on next boot, agree to this and restart the computer. when the chkdsk is done the computer will boot xp as normal, then logon and defrag, start, programmes, accessories, system tools, and defragment, i believe.

hope this helps

---

### Post by Speediakal on 2006-11-16
ok, so i defragged my both my drives and found that my D: drive was like all fragmented. but when i tried to install ubuntu, it still takes a really long time. How long is this supposed to take if i make a partition of 30GB?

---

