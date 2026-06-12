---
title: "finding hard drive space usage"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by grimdaze on 2005-10-12
probably a stupid question but how do i see how much hard drive space i have left

---

### Post by aysiu on 2005-10-12
There's probably a better way than this, but one way is to type this in a terminal ```
sudo fdisk -l
```

---

### Post by grimdaze on 2005-10-12
that just printed a bunch of stuff like this
16799: @ 0 for 0, type=0x0
16800: @ 0 for 0, type=0x0
16801: @ 0 for 0, type=0x0
16802: @ 0 for 0, type=0x0
16803: @ 0 for 0, type=0x0
16804: @ 0 for 0, type=0x0
16805: @ 0 for 0, type=0x0
16806: @ 0 for 0, type=0x0
16807: @ 0 for 0, type=0x0
16808: @ 0 for 0, type=0x0
16809: @ 0 for 0, type=0x0
16810: @ 0 for 0, type=0x0
16811: @ 0 for 0, type=0x0
16812: @ 0 for 0, type=0x0
Segmentation fault

---

### Post by mlomker on 2005-10-12
> that just printed a bunch of stuff like this


That isn't normal, fdisk -l should give you a list of your partitions.

I use this one to check disk usage.  

```

df -h

```

---

### Post by grimdaze on 2005-10-12
thanks df -h worked

---

### Post by aysiu on 2005-10-12
I'm glad that command worked for you, but mlomker's right. Your output for *sudo fdisk -l* is worrisome.

---

### Post by grimdaze on 2005-10-12
well what should i do about it....and how

---

### Post by aysiu on 2005-10-12
[QUOTE=grimdaze]well what should i do about it....and how[/QUOTE] I don't know. I'm wondering if somehow you might have typed -1 or -I instead of -l

(that's one, i, not L)

---

### Post by grimdaze on 2005-10-12
i typed -l as in (ell)
also copied it from your post and pasted, had the same result

---

### Post by az on 2005-10-12
If you oppen up the filemanager (places, home) you see how much free space there is on your disk, at the bottom

---

### Post by Wolki on 2005-10-12
[QUOTE=grimdaze]i typed -l as in (ell)
also copied it from your post and pasted, had the same result[/QUOTE]

I'd be careful if I were you. This is not necessarily a fatal error, but could be a sign of bad things to come. To be on the safe side, make a backup of your important data: likely everything will continue to work, but if your hdd should break you'll be glad you did.

---

### Post by grimdaze on 2005-10-12
ok thanks, i'll be sure to do that

---

