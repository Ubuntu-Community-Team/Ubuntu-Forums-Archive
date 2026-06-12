---
title: "Problem With Uninstalling"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by SolidusRegime on 2007-05-29
A friend of mine started to use Ubuntu 7.04 but it really isn't his thing. He is kind of computer illiterate so I am putting Windows XP back onto his PC. I have booted up using th CD, however, when going to use the partitioner, it says no disk drives are found.

However he has a 60GB sata drive that he used all for Ubuntu.

Any ideas?

---

### Post by taurus on 2007-05-29
Boot his machine with Ubuntu LiveCD, delete all the partitions and format his harddrive to ntfs.  Then, boot with XP CD and you should be able to install XP on it again.

---

### Post by SolidusRegime on 2007-05-29
What app do I run to delete the partitions and format as NTFS?

---

### Post by Inxsible on 2007-05-29
GParted. Its on the LiveCD
System -- > Administration --> GParted

---

### Post by SolidusRegime on 2007-05-29
Thanks for that. I've tryed convincing him to keep using Ubuntu, but hes a shockwave/flash programmer. And he prefers the WinXP interface.

Thanks again.

---

### Post by SolidusRegime on 2007-05-29
There came up with 2 drives. One was called /dev/sda1 and the other was /dev/sda2. I can delete and format the /dev/sda1 however the other one cannot be removed.

I removed it, and formatted it, then when booting up the windows xp cd, it still said no disks were found.

---

### Post by taurus on 2007-05-29
Can you post the output of these commands while in LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
free
```

---

### Post by SolidusRegime on 2007-05-29
Gah, this is such a pain in the ***. Hang on, I will get the outputs for you.

Honestly, you'd think Windows XP would recognize all disk formats..wouldn't you?

---

