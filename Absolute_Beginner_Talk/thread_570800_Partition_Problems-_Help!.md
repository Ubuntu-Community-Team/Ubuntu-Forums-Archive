---
title: "Partition Problems- Help!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by dvryan on 2007-10-08
I'm an intermediate Windows User but brand new to Ubuntu.

I just partitioned my hard drive using the Ubuntu CD, and was able to get a dual-boot system up and running, with Windows XP on one partition and Ubuntu on the other.  The problem?  I wanted the XP partition to be 80 GB, and the Ubuntu 20 GB.  I reversed this by accident, so now my Windows partition is almost full.  My question- ideally I could re-size both partitions to what I want without formatting/etc.  Is this possible?  If not, how do I take Ubuntu (and the partition) off so Windows has the entire disk space again?  If I could get to that point, at least I could re-do this, correctly sizing the partitions this time.

Thanks,
Dan

---

### Post by om1 on 2007-10-08
use your Ubuntu live cd..
boot to the live cd and there is a aplication in that called gpartition.... you can do it with that
back up all important files first.... if something like a power failure or something it can currupt all data....
there isnt any safer way to do that though

---

### Post by dvryan on 2007-10-08
Thank you for your help.  I tried using that program, and ran into several issues:
1) I tried to minimize the linux partition, and it encountered an error and wouldn't let me.
2) It wouldn't let me increase the windows partition- just reduce it.  This may be because, at present, my 2 partitions occupy the entire drive, but I'm not sure.  Since I haven't been able to reduce Linux, though, I won't know for sure.

---

### Post by om1 on 2007-10-08
make sure you dont have the partitions mounted.... are there icons on the desktop other than the install one? if so right click on them and choose unmount or eject first

---

### Post by dvryan on 2007-10-08
Forgive my ignorance- what does 'mounted' mean?

Yes, there are two other icons- both hard drives- that appear on the desktop.  If I unmount them, what does that do?  Does that erase any data on them?

Thanks,
Dan

---

### Post by om1 on 2007-10-08
no it will not erase them to unmount....
unmount is kindof like "safely remove" in windows... basically it makes it were you can not read and write to it... until you mount them... which you dont need to read or write to them for this
sorry if that doesnt make any since... its the best i can explain it

---

### Post by dvryan on 2007-10-08
That makes sense- thanks.  I'll try this and see what happens (bedtime where I live, so I'll try tomorrow).

Thanks again for your help-
Dan

---

### Post by om1 on 2007-10-08
no problem ... post to let us know if it fixes your problem or not
good luck

---

### Post by Shazaam on 2007-10-08
Do they show up on your desktop running the live cd? The only way for that to happen is if you manually mount them. The livecd runs in ram, an installed system runs off of the hard drive. So while running the livecd you have to manually "mount" the drives to access them and "umount" to disable access to the drives. Windows (and an installed flavor of linux) AUTOMOUNT the hard drives.
Post the terminal output of this..
```
sudo fdisk -l
```
(small L)

---

### Post by mivo on 2007-10-08
You can also download and burn the GParted Live CD (found [here]("http://gparted.sourceforge.net/livecd.php")), boot with it and do all the resizing without an OS running.

---

### Post by dvryan on 2007-10-08
I unmounted the drives and used gpartition on the linux cd with limited success.  I was able to re-size the linux partition this time, down to what I wanted it to be.  The problems:

1) I couldn't move the partition to the end of the hard drive
2) I couldn't increase the size of the windows partition

Right now, I have 1 windows (ntfs) partition, 1 linux (ext3, I think), and 1 unallocated (the result of decreasing my linux partition size).  Do I have to allocate this partition first?  I thought I'd have to move the linux partition first. . . 

Thanks,
Dan

---

### Post by dvryan on 2007-10-09
Does anyone have any ideas as to what may be going on here?

Thanks,
Dan

---

