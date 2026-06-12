---
title: "Hard Drive Formatting"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by meisbored on 2007-01-26
I want to format my internal hard drive from ext3 to fat32, but I can't figure out how to umount the drive like QTParted tells me too. When I go to the terminal and type "umount /dev/sda1"
it just says "umount: /dev/sda1 mount disagrees with the fstab".
Anyone know what to do?

---

### Post by taurus on 2007-01-26
What's the output of this command from a terminal?

```
df -h
```

---

### Post by rocknrolf77 on 2007-01-26
Why do you want to format your drive to fat32? It's an outdated filesystem. You can read and write ext3 from windows with [www.fs-driver.org](www.fs-driver.org)

---

### Post by meisbored on 2007-01-26
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  1.9G   99G   2% /
varrun                755M   92K  755M   1% /var/run
varlock               755M     0  755M   0% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                755M     0  755M   0% /dev/shm
lrm                   755M   18M  738M   3% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             299G   25G  274G   9% /media/LACIE

```

/dev/sdb1 is my external hard drive, /dev/sda1 is the big ext3 portion of my 120GB internal.

---

### Post by taurus on 2007-01-26
Then you can't unmount /dev/sda1 since Ubuntu is on it.  You have to unmount the /dev/sdb1.

```
sudo umount /dev/sdb1
```

---

### Post by meisbored on 2007-01-26
Unmounting the external hard drive seems pointless, I don't need to format it. It's already fat32. It's just that I want to be able to install Windows XP again and I can't do that with it all in ext3. Or I guess I could install it to the external or something...

---

### Post by taurus on 2007-01-26
You want to install XP on /dev/sda1!  Right now, you only have two harddrives, /dev/sda & /dev/sdb.  So, where do you want to install XP since you already have Ubuntu on /dev/sda1 (and swap is on /dev/sda5)?

---

### Post by meisbored on 2007-01-26
Well I guess I thought I could make a partition for Ubuntu on /dev/sda1 and install Windows on the same drive, as I think my friend knows how to go about doing that.

---

### Post by taurus on 2007-01-26
If you want to resize /dev/sda1, then you need to boot from the LiveCD and use gparted on the LiveCD to resize it.

---

