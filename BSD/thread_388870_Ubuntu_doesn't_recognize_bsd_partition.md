---
title: "Ubuntu doesn't recognize bsd partition"
date: 2007-03-20
forum: BSD
---

### Post by mmmichael on 2007-03-20
I installed freebsd 6.2 on hdb1 and then Ubuntu 6.10 on hda9.
When Ubuntu installed grub it recognized all the OSs on hda1-9, but not the freebsd.
It didn't show up in /etc/fstab either. When I try to manually mount it I get unknown file system.
Gparted also shows unknown fs. fdisk shows system as FreeBSD.

Any advise on editing /etc/fstab and /boot/grub/menu.lst so I can mount  or boot freebsd?

---

### Post by mips on 2007-03-20
I noticed the same thing yesterday. The partitionar on the alternative cd can do nothing with the bsd partition, no delete, no format etc.

---

### Post by angryfirelord on 2007-03-20
grub doesn't recognize ufs filesystems. You have to use this to add it:

title FreeBSD
rootnoverify(hd0,1) #Change this as necessary
chainloader +1
boot

However, I don't know how to mount it.

---

### Post by mmmichael on 2007-03-21
> **angryfirelord said:**
> grub doesn't recognize ufs filesystems. You have to use this to add it:

title FreeBSD
rootnoverify(hd0,1) #Change this as necessary
chainloader +1
boot
.

I did this and it got me to the freebsd boot options screen. It boots if I select safe mode, but if I select the default option it can't mount the kernel.:confused:

---

### Post by mephisto786 on 2007-03-31
Try without the noverify statement......worked on my PCBSD dual boot

good luck

---

### Post by hanzomon4 on 2007-03-31
> **angryfirelord said:**
> grub doesn't recognize ufs filesystems. You have to use this to add it:

title FreeBSD
rootnoverify(hd0,1) #Change this as necessary
chainloader +1
boot

However, I don't know how to mount it.

Yeah that worked for me, I don't think linux has support for the ufs or perhaps it's not compiled into the ubuntu kernel

---

### Post by rplantz on 2007-05-25
You have probably solved your problem, but I added the following to my menu.list:
```

# For booting FreeBSD 

title FreeBSD 
root (hd1,a) 
kernel /boot/loader 
boot

```
which boots my FreeBSD very nicely.

My Ubuntu is on a SATA disk and my BIOS is set to boot from that first. So grub is on that disk. I have FreeBSD on a PATA disk, hence the "hd1" in the root command above.

---

