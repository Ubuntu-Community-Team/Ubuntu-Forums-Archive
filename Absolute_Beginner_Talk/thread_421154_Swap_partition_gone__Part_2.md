---
title: "Swap partition gone : Part 2"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2007-04-24
Hello there! My ubuntu is running with no swap, and I really did not do anything. 

```
vinicius@imola:/$ free
             total       used       free     shared    buffers     cached
Mem:       1026584     722280     304304          0      90500     295588
-/+ buffers/cache:     336192     690392
Swap:            0          0          0
vinicius@imola:/$
```

during startup I get activating swap failed ...

here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=c3d5f81c-b2fb-4fd9-af67-7e3a1d5773ee / reiserfs notail 0 1
#/dev/sda5 -- converted during upgrade to edgy
UUID=1a048b00-ff5f-4dd2-848c-3a433283b801 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


```
I really did not understand this whole UUID thing, I'm used to plain /dev/sda noauto.... etc, and I'm guessing this is the problem (after reading some system messages)

here's the last line of my dmesg:

**[17179606.292000] Unable to find swap-space signature**

I've tried to restore the fstab using /dev/sda5 none swap sw 0 0 but did not work as well. Any ideas of why my swap space just vanished?

Regards

---

### Post by joft on 2007-04-24
What does
```

sudo fdisk -l /dev/sda

```
say? Perhaps your swap isn't sda5 anymore?

Perhaps you have to "reformat" the swap partition?
```

sudo mkswap /dev/sdaX

```

---

### Post by taurus on 2007-04-24
Or just replace

```
UUID=1a048b00-ff5f-4dd2-848c-3a433283b801 none swap sw 0 0
```
with

```
/dev/sda5   none   swap   sw   0   0
```

---

### Post by mcduck on 2007-04-24
Check that the UUID you have in your fstab for swap is correct. You can do that by running 'ls -la /dev/disk/by-uuid' 

Then run 'sudo mkswap /dev/sda5' and 'sudo swapon -a' & try if it's working with 'free -m'

---

### Post by viniciuscarvalho on 2007-04-24
> **mcduck said:**
> Check that the UUID you have in your fstab for swap is correct. You can do that by running 'ls -la /dev/disk/by-uuid' 

Then run 'sudo mkswap /dev/sda5' and 'sudo swapon -a' & try if it's working with 'free -m'

That did the trick, thanks, after that my swap is back :) :

```
             total       used       free     shared    buffers     cached
Mem:          1002        983         19          0         20        232
-/+ buffers/cache:        730        272
Swap:         1584          0       1584

```

Regards

---

