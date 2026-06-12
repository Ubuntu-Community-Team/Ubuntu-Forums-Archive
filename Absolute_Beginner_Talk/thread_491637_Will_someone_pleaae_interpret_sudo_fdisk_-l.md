---
title: "Will someone pleaae interpret sudo fdisk -l"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-03
I just installed ubuntu onto and old P3 and it seems to be working fine.  The PC previously had windows 2000 on it and I want to make sure that I completely wiped out the windows stuff.  Can someone please review the results of

```

sudo fdisk -l

```

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2389    19189611   83  Linux
/dev/sda2            2390        2482      747022+   5  Extended
/dev/sda5            2390        2482      746991   82  Linux swap / Solaris


and let me know whats going on and what it all means.

thx in advance,

VC

---

### Post by greg_g on 2007-07-03
Well, go ahead and give us the output of that command and we'll gladly take a look.

EDIT: ok, we'll take a look ;)

---

### Post by videocheez on 2007-07-03
> **greg_g said:**
> Well, go ahead and give us the output of that command and we'll gladly take a look.

oops.  I forgot:oops:

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2389    19189611   83  Linux
/dev/sda2            2390        2482      747022+   5  Extended
/dev/sda5            2390        2482      746991   82  Linux swap / Solaris

---

### Post by geek_Man on 2007-07-03
You can rest assured that Windows is gone.

---

### Post by scxtt on 2007-07-03
/dev/sda1 = your ubuntu install, the "root" of the filesystem
/dev/sda2 = extended partition (apparently for no reason)
/dev/sda5 = swap partition

---

### Post by videocheez on 2007-07-03
> **geek_Man said:**
> You can rest assured that Windows is gone.

Roger that!:D

---

### Post by videocheez on 2007-07-03
> **scxtt said:**
> /dev/sda1 = your ubuntu install, the "root" of the filesystem
/dev/sda2 = extended partition (apparently for no reason)
/dev/sda5 = swap partition

What do you mean *"/dev/sda2 = extended partition (apparently for no reason"* and where will this partition show up in my file system.  When i go to the filesystem it says that I have 15.8GB available.  Does this mean that ubuntu + all of the other apps take up approx 4GB of space?
If that sda2 partion is there for no reason, should i remove or merge it with another?

Thx in advance,

VC

---

### Post by scxtt on 2007-07-03
generally you'd only need an extended partition if you've filled up the primary partition layout (you can make 4 partitions in the primary partition), if you want more, you have to make an extended partition ... you haven't lost space or anything - but your partition scheme doesn't require that extended partition ...

you really only need to worry about that if you separate all the "major" directories into their own partitions: /, /var, /opt, /home, /tmp, etc. ... cause that would require more than the 4 partitions in the primary space ...

---

### Post by ecs_pf5 on 2007-07-03
Would his swap partition be living kinda 'inside' the extended partition (i.e. would it in fact be a very *bad* idea to remove the extended partition now, the way it has ended up?

Or could the extended partition be fairly simply deleted,,,, leaving the swap partition still in existence?

---

### Post by bradmayne on 2007-07-03
if your not totally sure of what your doing DO NOT use fdisk!!! There are many other partitioning utilities out there!!

---

### Post by scxtt on 2007-07-03
depends on how much ram he has (is swap ever touched?) ... if the extended partition is removed, swap is gone ... i can't remember if ubuntu will  boot or not w/o a swap partition - i know you can't continue w/ the install if you don't have one, not sure what happens if you "swapoff" after you've booted and then remove it in order to resize the primary ...

he really has no reason to rearrange it - it's not "wrong" to do it that way - just unnecessary ...

---

### Post by Benoone on 2007-07-04
> **scxtt said:**
>  (you can make 4 partitions in the primary partition), if you want more, you have to make an extended partition ... 

Generally, on a PC,  you can only have four partitions total and that includes the extended partition of which you can have only one so that's four primary or three primary plus one extended.  But... you can have many logical partitions (as your BIOS can handle - usually 20-26) enclosed inside your one extended partition. (whew)

If you do not do a manual partitioning using the alternative disk then Ubuntu will usually grab the first space available and make a primary partition for the / (root).  It is then smart enough to not use a valuable primary partition for the swap file so it makes a extended partition and puts it in there leaving you with the option of adding two more primary partitions later plus a bunch of logical partitions.

Ubuntu and most linux will boot from any partition so I usually put all my Linux in logical partitins (enclosed inside the extended partition) which then gives me the space for three primary partitions for Microsh!t OS's which cry tears and refuse to boot if not located there.

I hope this helps.

Regards

Benoone

---

### Post by scxtt on 2007-07-04
yeah, that's what i was driving @ ...

i ALWAYS choose my own partition scheme - so i didn't know about it automagically putting swap on a logical partition in the extended partition - pretty smart :)

---

