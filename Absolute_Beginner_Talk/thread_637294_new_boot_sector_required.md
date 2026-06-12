---
title: "new boot sector required"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by castlecrae on 2007-12-10
boot sector on hdd that died
os on sda with no boot sector
can read sda but grub cant find sda (sata hard disc)
can I write a boot sector on sda

---

### Post by castlecrae on 2007-12-10
sorry my first time on any forum
I am having trouble finding out if I can add a boot sector to a hard disk that only has a linux os on it as the disc that had the boot on it was a duel boot with windows and it died.
i suspect that I will have to reinstall but I dont want to do this if I dont have to
the disc is a sata disc is this a problem?

---

### Post by nikoPSK on 2007-12-10
Well, now you are talking in actual sentences. Could you make it more clear?

---

### Post by kelbizzle on 2007-12-10
Right now I have no grub at all. So I use the Gparted livecd when you boot to it theres options to boot directly from the partitions. I hope this helps. [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by sloggerkhan on 2007-12-10
at the very least you could resize the main partition on the drive (gparted, probably) and then install a bootloader to the new partition.

---

### Post by sloggerkhan on 2007-12-10
Na

---

### Post by Tyke91 on 2007-12-10
If you cannot boot into Ubuntu, get your live CD, pop it in and follow this procedure:

open a terminal when you get to the liveCD desktop and type this
```
sudo grub
```

then 

```
find boot/grub/stage1
```

this will give you a list of hard drives that look like this:

(hd?,?)  where the question marks are actual numbers (like (hd0,4) or something)

Choose the one for ubuntu (they're listed as you have them, so the top one would be your first partition, the second would be your second partition and so on)

when you have found the ubuntu one, type this

```
 root (hd?,?) 
```  replace the '?'s with the numbers for the ubuntu hard drive


finally, setup the MBR

```
 setup (hd0)
```


hope this works for you.

---

### Post by castlecrae on 2007-12-11
thank you for the reply

find boot/grub/stage1  

gave me 

error 15: File not found

did a df in terminal and got

Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   517892     33788    484104   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                   517892     33788    484104   7% /lib/modules/2.6.20-15-generic/volatile
varrun                  517892       104    517788   1% /var/run
varlock                 517892         0    517892   0% /var/lock
udev                    517892       120    517772   1% /dev
devshm                  517892         0    517892   0% /dev/shm
tmpfs                   517892       272    517620   1% /tmp
/dev/sda1            304682836   8423252 280782568   3% /media/disk

---

### Post by castlecrae on 2007-12-15
thanks for the help
yes this rebooted my machine
used gparted to read the disk to find the partition info
had to guess the hard drive number
but the new boot looks for hdd(3,0) how can I edit the boot record to look for hdd(1,0)

---

