---
title: "[SOLVED] Swap oddity"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by JillSwift on 2007-12-11
I'm not particularly worried about this as I've 2 gigs of memory and don't come close to pushing memory space.

But...

In my fstab I've got a swap partition mounted:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
proc /proc proc defaults 0 0
#
# Entry for /dev/sda4 : (rrrrrewt)
#
UUID=4c9451f0-6724-47a6-96dc-bf6e5a32d5fd / ext3 defaults,errors=remount-ro 0 1
#
# Entry for /dev/sda5 : (/home)
#
UUID=f1b22bea-fbbc-4674-82af-cfaeeff0e08a /home ext3 defaults,errors=remount-ro 0 1
#
# Entry for /dev/sda2 : (Bootable NTFS)
#
UUID=1C9CD1759CD149C2 /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
#
# Entry for /dev/sda6 : (Swap)
#
UUID=9b3c372c-c14e-bfb5-9557-037cb2165a12 none swap sw 0 0
#
# CD/DVD drives
#
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
```yet when I run "free" it says this:```
$ free
             total       used       free     shared    buffers     cached
Mem:       2074848    1026516    1048332          0      44956     395676
-/+ buffers/cache:     585884    1488964
Swap:            0          0          0
```Zip? Say what? That's a 2.5 gigglebyte partition there, bub.

Anyone have any idea what goeth on?

---

### Post by mcduck on 2007-12-11
First, run 'blkid' to get UUID's for all your partitions. Then make sure that the UUID your fstab has for swap is correct.

After that run 'sudo mkswap /dev/sda6' and 'sudo swapon -a'. Now the swap should work, confirm this by running 'free -m' again.

---

### Post by anaconda on 2007-12-11
I suspect that the uuid of your swap partition is not correct.
(it changes when you format the swap partition.)

try in terminal:
```
swapon /dev/sda6
```
and then try 
```
free
```
again..

---

### Post by taurus on 2007-12-11
Or just replace the **UUID=9b3c372c-c14e-bfb5-9557-037cb2165a12** with **/dev/sda6** in /etc/fstab.

```
gksudo gedit /etc/fstab
```

---

### Post by JillSwift on 2007-12-11
Wow. I really had no idea you could refer to the drives in fstab via their /dev entry. Kewlies! =^_^=

Yes, the UUID had changed. All is well in swapland! Thank you all!

---

### Post by jaybombalous on 2007-12-11
> **taurus said:**
> Or just replace the **UUID=9b3c372c-c14e-bfb5-9557-037cb2165a12** with **/dev/sda6** in /etc/fstab.

```
gksudo gedit /etc/fstab
```

this is not the best solution at all. I had a problem once where my machine was trying to boot up in arch and trying to load ubuntu at the same time. Thats because I used the physical device location and since my bios swaps the position depending on which device boots first, there was a major hiccup. This is why u can't count on physical drive locations and the need for persistent drive naming schemes.

BTW, they are phasing out hda block devices, soon all will be sda, because of this backwards compatibility with hda devices will need to use persistent block device naming schemes.

lets start informing the masses about the future so we don't create more problems then we need. :)

---

