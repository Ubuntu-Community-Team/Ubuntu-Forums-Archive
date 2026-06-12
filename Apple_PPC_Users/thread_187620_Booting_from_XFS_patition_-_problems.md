---
title: "Booting from XFS patition - problems"
date: 2006-06-03
forum: Apple PPC Users
---

### Post by Adapted.Cat on 2006-06-03
I just installed Kubuntu 6.06 on an iBook.

The graphical partitioner has problems, as others have noted, but I got around that using fdisk. The installer didn't seem to recognise that I had a bootstrap partition even though I had one, but I pressed on anyway.

I set up the installation to use an XFS partition I just created. Everything installed according to plan. So I rebooted.

As soon as it booted into linux, I got a kernel VFS panic, unable to mount filesystem.

So I rebooted from the CD (by the way, "rescue" does not work - I had to use "live") and ran yabootconfig by hand to ensure everything was okay on that front. I then ran "gunzip -c /boot/initrd.img | cpio -t | less" to see what filesystem modules would be available at boot time. Sure enough xfs.ko is there, so there should be no problem booting into it.

Next time I reboot, the kernel stuff gets a little further, but after reading in the initrd, it tries to mount the root partition and again panics "unable to mount" and reboots after a while.

I've checked out the XFS partition myself - nothing is wrong with it. Obviously yaboot doesn't have a problem with it either, and the kernel manages to load initrd.img from it but then it can't mount it.

Anybody know what is going on here?

---

### Post by Adapted.Cat on 2006-06-03
Some more information on my boot problems: Just before I get the kernel panic I see:
```

RAMDISK: incomplete write (-28 != 32768) 8388608
VFS: Cannot open root device "hda7" or unknown-block(0,0)

```
This means that the RAMDISK size in the kernel config is set too small. I tried re-installing the kernel from the apt repositories, but no joy there. I also tried trimming the initrd.img down a bit, but that didn't help either.
The initrd from apt is actually smaller than the one on the install CD, and the kernels are identical, so the initrd size can't be the root of this problem. I then noticed an initrd-size keyword in yaboot.conf, so I changed this, re-ran ybin, and suddenly that RAMDISK error message has disappeared.

Unfortunately the kernel panic remains.

Are XFS filesystems not supported at boot-up?
If not, what filesystems are?

---

### Post by Adapted.Cat on 2006-06-03
I finally fixed the problem by reinstalling from scratch onto a reiserfs partition.
Once the install is finished, mount the partition onto /mnt, and 
```

cp /mnt/etc/yaboot.conf /etc
ybin
umount /mnt
sync
reboot

```

Rebooted and worked like a dream (at last)!

---

### Post by Ptero-4 on 2006-06-03
That's gotta be a regresion bug. Hoary supported xfs correctly, but both breezy and dapper seems to have problems with xfs.

---

