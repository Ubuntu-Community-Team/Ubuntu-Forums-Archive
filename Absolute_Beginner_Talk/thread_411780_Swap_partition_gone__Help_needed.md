---
title: "Swap partition gone : Help needed"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2007-04-17
Hello there! Few days ago I did something really stupid. I was lacking space, and the .thrash directory had over 10 gigs of space, so I went there and just rm -Rf *, thinking that nothing could happen, after all that was a thrash dir....

Coincidence or not, right after that, my linux start acting REALLY slow. To open a single document of 4kb, took over 15 seconds, when I start heavy app that rely on large config files, it took over minutes and the processor was not even being used.

Well, I've start to notice that the initial messages displayed:

Activating Swap [failed]

So  guess my swap partition has just gone, and that might be the reason. I'm looking for some guidance on how to proceed.

Any hint, advice, link, tutorial would be really great appreciated

Best regards

---

### Post by freebird54 on 2007-04-17
Try this code to see what's there...

```
sudo fdisk -l
```

Should have some similarities to this:

```
freebird@roost:~$ sudo fdisk -l
Password:

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3824    30716248+   b  W95 FAT32
**/dev/hde2            4869        5129     2096482+  82  Linux swap / Solaris**
/dev/hde3            5130       19457   115089660   83  Linux
/dev/hde4            3825        4868     8385930   83  Linux

Partition table entries are not in disk order
```

The bolded entry is what you hope to see :)

---

### Post by tommcd on 2007-04-17
Also, typing "free -m" will give the staus of RAM usage, including, swap, in megabytes. If you see no swap you can create a new swap with:

sudo mkswap /dev/sda*
sudo swapon /dev/sda*

Replace * with the partition number for your swap, and change to hda* if your "fdisk -l" lists partitions as hda (IDE hard drive) instead of sda (sata hard drive).

---

### Post by regomodo on 2007-05-04
> **tommcd said:**
> Also, typing "free -m" will give the staus of RAM usage, including, swap, in megabytes. If you see no swap you can create a new swap with:

sudo mkswap /dev/sda*
sudo swapon /dev/sda*

Replace * with the partition number for your swap, and change to hda* if your "fdisk -l" lists partitions as hda (IDE hard drive) instead of sda (sata hard drive).

Awesome. Cheers for that. I had to do this a long time ago but forgot what to do. I knew it was easy to do but got miffed off cus i couldn't figure it out

---

### Post by kmoffat on 2007-05-06
This method allowed my to activate swap manually, but I now have a problem with the /etc/fstab entry (apparently) since after reboot the swap does not activate and I get the following error:

$ sudo swapon -a
Password:
swapon: cannot find the device for /dev/disk/by-uuid/UUID=cae610a9-672c-4525-b12c-2f4b16be6c23

I updated the fstab to the uuid that mkswap returned, but no help. 

swapon /dev/hda3 works fine.

What is all this UUID stuff, and how can I fix my fstab file?

Thanks!
ken

EDIT: changed the UUID entry to the actual swap partition (/dev/hda3), which works on reboot.

---

