---
title: "[SOLVED] Is it possible to have more then 4 partitions on one hardrive?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by spydon on 2008-01-21
Hey there.
My harddrive is partioned like this:
Ubuntu root - sda1
Minu root - sda2
Home - sda3
Swap - sda4

It's a 250gb harddrive and now I doesn't seem to be able to make more partitions...
Am I just doing something wrong or is their some kind of restrivtion of how many partitions you can have on one harddrive?
I would atleast like to tripple- or quad-boot the comp.

---

### Post by overdrank on 2008-01-21
> **spydon said:**
> Hey there.
My harddrive is partioned like this:
Ubuntu root - sda1
Minu root - sda2
Home - sda3
Swap - sda4

It's a 250gb harddrive and now I doesn't seem to be able to make more partitions...
Am I just doing something wrong or is their some kind of restrivtion of how many partitions you can have on one harddrive?
I would atleast like to tripple- or quad-boot the comp.

HI and as I understand it you can have 4 partitions to a hard drive unless you create a extended partition then you may create more partitions with in the extended partition. This link has good info
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by bumanie on 2008-01-21
You can only make four primary partitions on a hard drive, on top of that, as overdrank says, it is possible to make any number of partitions within an extended partition.

---

### Post by thelatinist on 2008-01-21
> **bumanie said:**
> You can only make four primary partitions on a hard drive, on top of that, as overdrank says, it is possible to make any number of partitions within an extended partition.

To clarify, in that case you can have only three primary partitions and one extended partition with any number of logical partitions within it.

---

### Post by spydon on 2008-01-21
Is it possible to install linuxes on the logical partitions then?

---

### Post by asmoore82 on 2008-01-21
I believe Linux can be anywhere but the /boot directory *might*
have to be a primary partition for GRUB to function; which would
be a limitation of BIOS tools that GRUB has to work with.

---

### Post by thelatinist on 2008-01-21
> **asmoore82 said:**
> I believe Linux can be anywhere but the /boot directory would
have to be a primary partition for GRUB to function; which
is a limitation of BIOS tools that GRUB has to work with.

Really? I could swear I first installed Ubuntu with / on a logical partition.

---

### Post by wolfen69 on 2008-01-21
> **thelatinist said:**
> Really? I could swear I first installed Ubuntu with / on a logical partition.

that would mean grub is located on one of your primary partition. not your ubuntu install.

---

### Post by bumanie on 2008-01-21
I believe I have read that ubutnu can boot from within a logical partition. Windows needs a primary partition, but grub doesn't (apparently).

---

### Post by imon9 on 2008-01-21
i comfirn ubuntu can run from logical partition (extended partition)
coz mine is running like this now...all 3 linux partition root, swap, and home all in the same extended partion :)

not sure about grub tho, i just let it install on the same hd, i assume every drive have essential set the first part of the disk as MBR

---

### Post by asmoore82 on 2008-01-21
> **imon9 said:**
> i comfirn ubuntu can run from logical partition (extended partition)
coz mine is running like this now...all 3 linux partition root, swap, and home all in the same extended partion :)

not sure about grub tho, i just let it install on the same hd, i assume every drive have essential set the first part of the disk as MBR

I'm glad to be proven mistaken on this one: just one more uber-Linux ability!
could you post the output of ```
mount
```

---

### Post by spydon on 2008-01-21
Here is the mount output:
```
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /home type ext3 (rw,usrquota)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

```

---

### Post by thelatinist on 2008-01-21
> **wolfen69 said:**
> that would mean grub is located on one of your primary partition. not your ubuntu install.

If you are referring to stage 1, that is always located in the MBR, isn't it?  If you are referring to stage 1.5, that is located in the first 30 KB directly following the MBR, no matter what partition is physically first on the disk, right?  If you are referring to stage 2, which is located in the /boot/grub folder (which is what asmoore82 was talking about), then, no, /boot/grub resided on a logical partition.

---

### Post by spydon on 2008-01-21
Awesum! Now I'm quad-booting and it works like a charm, thx everybody!

---

