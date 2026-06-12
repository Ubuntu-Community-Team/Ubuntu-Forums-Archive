---
title: "Ubuntu doesn't recognize disk"
date: 2011-06-05
forum: Apple Hardware Users
---

### Post by canhoto on 2011-06-05
Hi.

I installed a [SIZE=1]Ultra ATA-133 IDE Adapter ACARD AEC-6280M in my Power Mac. With it, I can have big hard drives installed without the 128 GB limitation of the built-in bus.

It works fine but, when trying to install Ubuntu on a second hd (attached to the adapter), the installer doesn't see any disks, telling me that I don't have enough space. I think it must be some kind of problem between Ubuntu (or the installer) and the adapter. 
Of course I can always attach the two drives to the original bus, but I will loose the extra space (I have a 160 GB and a 400 GB...).

I tried to attach one to the original bus and the other to the adapter, but it only recognises the drive attached to the original bus.

Any ideas?
[/SIZE]

---

### Post by linuxopjemac on 2011-06-05
There have been troubles with this adapter in the past as well. I guess it's a kernel issue, not having the right module compiled. If you don't want to compile your own kernel, you might just want to try Debian, it should have support for this PCI adapter.

[https://launchpad.net/bugs/65978](https://launchpad.net/bugs/65978)

In any case you would want a kernel with the following options:
CONFIG_BLK_DEV_AEC62XX=y

or as module:

CONFIG_BLK_DEV_AEC62XX=m

I know that in my Debian kernel (2.6.32) running under MintPPC, the module is compiled in (CONFIG_BLK_DEV_AEC62XX=m). I can modprobe it:
```
sudo modprobe aex62xx
```
and it shows up then:
```
lsmod
Module                  Size  Used by
aec62xx                 6645  0
```

[http://cateee.net/lkddb/web-lkddb/BLK_DEV_AEC62XX.html](http://cateee.net/lkddb/web-lkddb/BLK_DEV_AEC62XX.html)

---

### Post by linuxopjemac on 2011-06-05
update: I looked at some Ubuntu kernels. They don't have support built in for this PCI adapter card.

I saw a bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329864)
[http://www.mailrepository.com//ubuntu-bugs.lists.ubuntu.com/msg/2526654/](http://www.mailrepository.com//ubuntu-bugs.lists.ubuntu.com/msg/2526654/)

---

### Post by canhoto on 2011-06-06
I tried to install Debian, and it recognizes the disks. However, I wasn't able to complete the installation, because, at a certain moment, it says that it's unable to complete the yaboot installation. I tried it with both the CD and the DVD installer. I have always this message at a certain point. Maybe I should put the question on a Debian forum? Anyway, that's like you said - no support for this card with Ubuntu.

---

### Post by linuxopjemac on 2011-06-07
You can install yaboot manually. For that you have to boot into a liveCD (I would take Finnix), it's a great small iso that works well. Then you chroot into the newly created Debian system and adapt /ctc/yaboot.conf if needed and run ybin -v. Maybe it's better to take a Debian LiveCD, as it will be more likely that the kernel has support:
[http://live.debian.net/archive/images/6.0_alpha2/powerpc/iso/debian-live-60alpha2-powerpc-standard.iso](http://live.debian.net/archive/images/6.0_alpha2/powerpc/iso/debian-live-60alpha2-powerpc-standard.iso)

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

