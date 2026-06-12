---
title: "HFS Partition Does Not Mount at Bootup"
date: 2006-06-30
forum: Apple PPC Users
---

### Post by mooreted on 2006-06-30
I have gone over my fstab, and can't seem to find the problem. My HFS+ partition does not mount automatically when I boot into Ubuntu.

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3       /media/mac      hfsplus user,auto,rw,umode 0 0

---

### Post by tidris on 2006-06-30
Make sure directory /media/mac already exists.

---

### Post by mooreted on 2006-07-01
Yes, it is there. I can mount it fine from the CLI, it just won't mount at bootup.

Thanks.

---

### Post by mooreted on 2006-07-02
So, anybody? My fstab looks fine, why no mount at bootup?

---

### Post by xurios on 2006-07-04
What exactly are you typing at the CLI? Doesn't umode require an assignment?

This works for me:

/dev/hda3	/media/Gato	hfsplus rw,user,auto 	0	0

---

### Post by mooreted on 2006-07-08
Thanks. I have tried it without the umode switch. Still have to boot my hand.

From the cli its: sudo mount -t hfsplus /dev/sda3 /media/mac

---

### Post by pindar on 2006-07-09
I'll tell you a very personal experience: on a gentoo PPC, I had my hfsplus partition in fstab. It would mount automatically, but I had lots of problems, up to the point that I couldn't boot into OS X anymore. I said to hell with it, took it out of fstab and mounted it by hand - never had any trouble again. So my personal advice would be: save yourself some headaches and mount it by hand, it's only 5 seconds. Or stick a command into your .profile to make it mount when you log in; if mounting by hand works, this should work too. 

Apart from that a shot in the dark: you're aware that newer kernels can't mount journaled hfsplus filesystems rw? Could that be the cause.

---

### Post by Gen2ly on 2006-12-02
Haven't been able to mount either through fsck either using 6.10,

I found another way besides yours Xurios, though I haven't tried them yet.  Is there any sage wisdom about which one is best considered?

> /dev/hda11 /media/Macintosh_HD hfsplus rw,exec,auto,users 0 0
/dev/hda# /mount/### hfsplus defaults,noatime 0 0

I've used the first code for a week now and it works, no problems.

NOTE: Don't do like I did and edit fstab with this partition/drive mounted.  Though I was able to find a way to umount (had add old values back into fstab.)

---

