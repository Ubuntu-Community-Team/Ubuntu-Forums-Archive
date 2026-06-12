---
title: "/home on seperate partition?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Evil Whisper on 2005-12-21
Hello!

I would like to move the home directory to a new partition away from the other system files.  Could somone help walk me through this?

I'll be using a Ubuntu LiveCD and gParted to change the partitions.

Also if I do move the home directory onto a new partition is it possible for me to completely re-install ubuntu and maintain the current home directories?


One More Thing:  Could somone also help me set up a small partition for me to test dapper on?


Thanks In Advanced,
- Evil Whisper

---

### Post by joshuapurcell on 2005-12-21
We would need to know what your filesystem looks like now. Do the following commands and post the results:

sudo fdisk -l

sudo df -h

---

### Post by lleb on 2005-12-21
[QUOTE=Evil Whisper]Hello!

Also if I do move the home directory onto a new partition is it possible for me to completely re-install ubuntu and maintain the current home directories?

Thanks In Advanced,
- Evil Whisper[/QUOTE]


yes, that is one reason for having seperate partitions when you build the system.  i almost always use the following:

/boot
/swap
/
/home

you want boot and swap as the first two partitions, then root should be next with home further out on the disk unless it is on a seperate disk, then you would move it as far forward as you can, or put it next to swap

example:

hda you could put /boot and /
hdb put /swap and /home

that would give ideal performance for the most part of a server and even for most workstations.

---

### Post by Evil Whisper on 2005-12-21
Ok since my post I've burnt a backup cd of my home directory and re-installed Ubuntu.  With the partition manager in the installer I created the following:

```

/
/home
/swap

```

Then I also toggled the boot flag to **ON** for the / partition.

**fdisk -l:**
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9729    78148161    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/hda6               1         608     4883665+  83  Linux
/dev/hda7   *         609        9541    71754291   83  Linux

```

**df -h:**
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7              68G  1.8G   63G   3% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda6             4.6G  136M  4.3G   4% /home

```

Have I set everything up correctly?

Also will there be any issues performance or otherwise by not creating a seperate /boot?

---

### Post by Sutekh on 2005-12-21
Looks good, but I would have given less space to /, and much more to /home, but it's no big deal.

A separate /home partition is a *very* useful thing I think.

Don't know about performance with a separate /boot partition; but if you ever wanted to in the future, why not?  It doesn't need to be very big at all.

---

### Post by Evil Whisper on 2005-12-21
Thanks Guys,

One more question,  If I wanted to resize both partitions how would I go about doing so?  Would I need a live CD and then use Gparted?  Or would that cause data loss?

Edit: Would it also be possible to create another small partition for Wine?

Thanks,
- Evil Whisper

---

### Post by Sutekh on 2005-12-21
[QUOTE=Evil Whisper]Thanks Guys,

One more question,  If I wanted to resize both partitions how would I go about doing so?  Would I need a live CD and then use Gparted?  Or would that cause data loss?[/QUOTE]
LiveCD with Gparted would be the way to go.  I'm not 100% sure about this, but I think that gparted should allow you to resize partitions without data loss. 

[QUOTE=Evil Whisper]
Edit: Would it also be possible to create another small partition for Wine?

Thanks,
- Evil Whisper[/QUOTE]
Absolutely.

---

### Post by Evil Whisper on 2005-12-21
Hello,

Sorry for asking so many questions but.
How would I get wine to install to that partition?
When ever i type:
```

sudo apt-get install wine

```

Then run wine it automatically puts it in my home directory.

---

