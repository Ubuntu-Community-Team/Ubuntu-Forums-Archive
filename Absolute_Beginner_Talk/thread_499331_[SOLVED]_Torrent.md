---
title: "[SOLVED] Torrent"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by vsugadhan on 2007-07-12
Hey,
my net connection suffers badly, so it stops in b/w for hours.... and my torrent stops whether it was in azureus or in utorrent(using wine)....i get an error .. error : write protected
any way to avoid this...

---

### Post by Al3xK3aton on 2007-07-12
You need to make sure the directory you're writing to is not write protected. I believe you can fix this from the root account.

---

### Post by vsugadhan on 2007-07-12
Mmmm ... Sorry...to ask...but I was downloading it to my windows partition.... and i dont know where to set the permissions...did a search..although i found some stuff...couldnt make head or tails of it...

---

### Post by Ek0nomik on 2007-07-12
> **vsugadhan said:**
> Mmmm ... Sorry...to ask...but I was downloading it to my windows partition.... and i dont know where to set the permissions...did a search..although i found some stuff...couldnt make head or tails of it...

If it is your Windows partition, then the file system of that partition is NTFS.  As a result, you need to enable write support for your NTFS drive, because Linux won't do it out of the box.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by vsugadhan on 2007-07-13
Hey thanks.... Problem solved....

---

### Post by Inxsible on 2007-07-13
> **vsugadhan said:**
> Hey thanks.... Problem solved.... Please mark the thread as solved, so someone else with a similar problem could make use of it. :)

---

