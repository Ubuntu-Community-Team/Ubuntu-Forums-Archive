---
title: "Macbook Swap Space? (Urgent!)"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by iAtari on 2008-02-28
I'm installing Gutsy on my 2.2Ghz Santa Rosa Macbook, and its already running OS X. The guide i'm using:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

doesn't mention a swap partition, and says that boot camp will cause problems if i have more then two partitions in total. I have enough space to create one, but will having the swap space screw up the dual-booted system? 

Thanks, 

iAtari

---

### Post by berniejv on 2008-02-28
I've installed on a new iMac, which is largely the same...  you can install without swap space, but the hibernate mode requires it.  Typically /swap should be at least as big as the amount of RAM you have installed.

check these instructions:

[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

In steps 6 and 7, adjust the sizes to give you swap space equal to the amount of RAM you have.  Should work from there.

Good luck!

---

### Post by berniejv on 2008-02-28
...also note the special link at the top for the Santa Rosa MacBook (your original link?)

anyhow, the partitioning should go the same as the previous link (inside step 6 of your instructions).

---

### Post by cyberdork33 on 2008-02-28
You don't have to use boot camp. All it does is partition. 

If you want to create a space with Ubuntu, do it, then boot the Ubuntu Live CD, start the partition editor and delete the partition you made. Then start the installer and tell it to use the free space. It will automatically create the root and swap partitions.

---

