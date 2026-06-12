---
title: "Adding Windows to GRUB"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by ma312 on 2007-10-09
I recently reinstalled windows and found, of course,  that it had in all of its arrogance set itself to boot without so much as giving me the chance to boot Ubuntu.  I used the live CD to install GRUB, and now I can start Ubuntu, but it doesn't give me the option to start windows.  I downloaded SuperBootDisk, so now I can boot windows with a CD, but I would like to add the option of booting windows to GRUB.  How do I go about doing this?

---

### Post by OffAxis on 2007-10-09
you just need to add an entry to your grub **menu.lst** file with the location of the windows boot.

```
sudo nano /boot/grub/menu.lst
```

you can add the entry to the bottom (that's where mine is)

here's mine

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

my windows is on a separate hard drive (sda1).

The syntax is (hard drive, partition)

---

### Post by ma312 on 2007-10-09
How do I find the location of my windows partition?  I know it's on a separate partition on my main hard drive, but what does that translate to?

---

### Post by skymera on 2007-10-09
ok what partittion?

partition 1 = 0 in grub
partition 2 = 1 in grub
partition 3 = 2 in grub
etc  etc etc

---

### Post by forestpixie on 2007-10-09
grub shows hdd first then partition

so following the same convention as skymera has shown

first hdd and first partition would be (hd0,0)

if you're in ubuntu try running

```
sudo fdisk -l
```

---

### Post by ronmarley1 on 2007-10-09
For future reference, if this happens again, you may want to try the Super GRUB Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
It'll search your hard drive and find your old GRUB and restore it to the MBR without having to reinstall GRUB.

---

### Post by crav on 2007-10-09
I have a similar problem. My grub recognizes and can boot into windows, but windows replaces grub's bootflag with it's own, I can't boot to grub until I use the liveCD again.

Anyone know how to fix this?

---

### Post by ronmarley1 on 2007-10-09
> **crav said:**
> I have a similar problem. My grub recognizes and can boot into windows, but windows replaces grub's bootflag with it's own, I can't boot to grub until I use the liveCD again.

Anyone know how to fix this?

I had the same issue.  Just about every time I booted windows, GRUB would get corrupted and I'd have to restore using the Super GRUB Disk.  In my case, I think the problem was TrendMicro on the Windows side not liking GRUB on the MBR.  I finally found this thread on the forums:
[http://ubuntuforums.org/showthread.php?t=469243](http://ubuntuforums.org/showthread.php?t=469243).  The thread had a solution found at [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) which worked for me.

---

