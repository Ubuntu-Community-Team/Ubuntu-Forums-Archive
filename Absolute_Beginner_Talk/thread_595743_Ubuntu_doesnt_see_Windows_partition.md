---
title: "Ubuntu doesnt see Windows partition"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Griffongob on 2007-10-29
hey all. Like many I decided to just upgrade from 7.05 to 7.10. Bad mistake as Beryl went crazy and refused to work and ubuntu no longer saw my windows partition along with many other issues. So I did a fresh install getting rid of my old ubuntu partition and making a new one. Everything worked out except ubuntu still doesnt see my windows partition. Has anyone else come across this problem, if so could you give me a hint on what to do to fix it. Thanks!

---

### Post by JBAlaska on 2007-10-29
Please post the output of ```
fdisk -l
```

---

### Post by Griffongob on 2007-10-29
fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


Thats what it outputs

---

### Post by CSMatt on 2007-10-29
The upgrade script should have removed Beryl for you if you used the version from the repositories.

---

### Post by Griffongob on 2007-10-29
Well with the fresh install everything works fine I switched to using Compiz fusion, which is what i wanted to do in the first place. Now if I could just get ubuntu to see my windows partition that would be perfect

---

### Post by JBAlaska on 2007-10-29
that command is fdisk -l not fdisk -i (lowercase L)

---

### Post by Griffongob on 2007-10-29
well using the command fdisk -l (lower case L) gives me nothing

---

### Post by JBAlaska on 2007-10-29
You should get output like this;
```
root@AMD64-Ubuntu:/etc# fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab88ab88

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          96        6397    50620815    7  HPFS/NTFS
/dev/hda2            6398        7976    12683314+  83  Linux
/dev/hda3            9543        9729     1502077+  82  Linux swap / Solaris
/dev/hda4            7977        9542    12578895   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a85e0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sda2           15201       30401   122102032+   f  W95 Ext'd (LBA)
/dev/sda5           15201       30401   122102001    7  HPFS/NTFS

```

---

### Post by CSMatt on 2007-10-29
I'm not so familiar with Fdisk, but what does this give you?
```
ls /dev/sd*
```

---

### Post by Griffongob on 2007-10-29
Is "root@AMD64-Ubuntu" your desktop directory? Sorry I'm still very new to all this >.<

---

### Post by Griffongob on 2007-10-29
> **CSMatt said:**
> I'm not so familiar with Fdisk, but what does this give you?
```
ls /dev/sd*
```

It gives me /dev/sda

---

### Post by stchman on 2007-10-29
> **Griffongob said:**
> hey all. Like many I decided to just upgrade from 7.05 to 7.10. Bad mistake as Beryl went crazy and refused to work and ubuntu no longer saw my windows partition along with many other issues. So I did a fresh install getting rid of my old ubuntu partition and making a new one. Everything worked out except ubuntu still doesnt see my windows partition. Has anyone else come across this problem, if so could you give me a hint on what to do to fix it. Thanks!

Follow my tutorial on mounting NTFS partitions in Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by CSMatt on 2007-10-29
Yeah you will need to use type sudo before the fdisk -l.  That gives you root (administrator) access for a short time.
```
sudo fdisk -l
```

---

### Post by jusmurph on 2007-10-29
> **Griffongob said:**
> Is "root@AMD64-Ubuntu" your desktop directory? Sorry I'm still very new to all this >.<

You need to enter it in the terminal.

---

### Post by CSMatt on 2007-10-29
> **Griffongob said:**
> It gives me /dev/sda

Odd.  Try
```
ls /dev/hd*
```

---

### Post by Griffongob on 2007-10-29
AH! ok now I get

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         574       33787   266791455    7  HPFS/NTFS
/dev/hdb2               1         573     4602591    b  W95 FAT32
/dev/hdb3           33788       38670    39222697+  83  Linux
/dev/hdb4           38671       38913     1951897+   5  Extended
/dev/hdb5           38671       38913     1951866   82  Linux swap / Solaris

---

### Post by Griffongob on 2007-10-29
> **stchman said:**
> Follow my tutorial on mounting NTFS partitions in Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

TYVM! Followed intructions to the letter and it worked great. Thanks everyone!

---

### Post by CSMatt on 2007-10-29
Never mind.

---

