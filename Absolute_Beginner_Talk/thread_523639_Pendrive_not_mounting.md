---
title: "Pendrive not mounting"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-08-12
Hi,

I have an pendrive which is not mounting... I tried to format it again but still does not show ... cfdisk shows fatal error and does not start

dmesg shows pendrive at sdb but I cannot mount it.. in recovery console

Is there a way to repartition it and format it again?

MrG

---

### Post by cetheriel on 2007-08-12
sure, 
[CODE]sudo apt-get install gparted{/CODE]
then run it. select the pendrive on right-top corner (sdb, isn't it?) and format it FAT16,
other filesystems may not work.

---

### Post by MrGreen on 2007-08-13
```
 6297.340862] sdg: Mode Sense: 00 00 00 00
[ 6297.340863] sdg: assuming drive cache: write through
[ 6297.341112] sdg : READ CAPACITY failed.
[ 6297.341113] sdg : status=0, message=00, host=1, driver=00 
[ 6297.341116] sdg : sense not available. 
[ 6297.341350] sdg: Write Protect is off
[ 6297.341353] sdg: Mode Sense: 00 00 00 00
[ 6297.341355] sdg: assuming drive cache: write through

```

Cannot mount or cfdisk /dev/sdg thinking drive is toast ;-(

Help!

MrG

---

