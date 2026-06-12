---
title: "Swap space on MacBook Air 6,1"
date: 2015-11-17
forum: Apple Hardware Users
---

### Post by drew37 on 2015-11-17
I recently installed Xubuntu 14.04 on a MacBook Air (6,1).

- Prior to installation I retained 30GB for OS X Yosemite, from Disk Utility I formatted the remaining space as "Free Space."
- Made my Xubuntu USB via the Unetbootin application
- Selected "Install"
- Got to the partitioning and split "Free Space" into two partitions, one 4GB marked as Swap and the remaining as ext3 and set to '/'
- Rebooted, all works well, my concern is the following

I was configuring Conky and noticed when listing Swap in use it reports I have no swap.. what's the easiest way to check this? Did I even need to create swap? I am running an i7 / 8GB of RAM. Prior to setting swap the Xubuntu installer would fail. If I don't need it I guess I'd like to take back that unused 4GB of space..

Thanks for any help!

---

### Post by flocculant on 2015-11-17
Check what it says in /etc/fstab

```
grep swap /etc/fstab
```

---

### Post by drew37 on 2015-11-17
Hey, I receive the following

```
# swap was on /dev/sda4 during installation
#UUID=myUUID none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by flocculant on 2015-11-18
So you do have swap, no idea why conky doesn't see it - never used it. 

If you want to get help with that - I'd start a new thread about it.

---

### Post by drew37 on 2015-11-18
Good to know that it is at least properly set, I'll mess around a bit and see if I can figure it out before polling the public.

---

### Post by drew37 on 2015-11-18
Got it! So I installed gparted, noticed it wasn't formated.. which was odd as I applied it as swap during the installation phase. However, I was able to format as swap, applied, then was able to set "swapon" to that partition and Conky etc began recognizing it. Alls well!

Side rant: I do love Linux, as annoying as this would be to most, it's a never ending learning experience.

---

