---
title: "MB Pro, OSX/Kubuntu access to shared partion?"
date: 2007-02-23
forum: Apple Intel Users
---

### Post by NickK1066 on 2007-02-23
I'm on the verge of purchasing a MacBook Pro 15" as a unix development system (GCC/CTM) as well as OSX with MS office.

In short I want to dual boot OSX and Kubuntu with a shared area between the two.

I need to use BootCamp to allow hardware access to the X1600 (CTM development) but I really would like the source code area to be shared between the kubuntu and OSX using mount points on both kubuntu and OSX.

So I'd like to partition 200GB as:
1. OSX partition 80GB
2. Kubuntu partition 80GB
3. Development partition 40GB

Has anyone done this?

Also does anyone know if they're bringing out Visio on OSX as well as Office 2008?

Cheers,
Nick.

---

### Post by Gen2ly on 2007-02-24
Nick I've doddled with this a little bit.  I dual-boot OS X and Ubuntu and have a third partition for Sharing.  I used HFS+ - WHICH WAS NOT A BRILLANT IDEA.  Since OS X and Ubuntu hand a users priveledges differenly, I have a lot of you don't have the necessary privleges... blah blah.  I haven't tried it but I hear the using and MS - DOS filesystem is the best way about it.  It doesn't have file-permissions, low disk size limitations, and both OS's have an ability to read and write to it.

If you try it Nick I'd like to know how it does.  i.e. stability, any special little tidbits to make it run alright?

---

### Post by siepo on 2007-02-24
I use FAT32 for file exchange between osx and linux because I don't fully trust Linux writing to hfsplus. In cases where Unix permissions matter to me, e.g. for development, I package data to .tar.gz or .tar archives before placing them there. Which is a hassle.

For e.g. multimedia files and disk images, I put up with DOS permissions and use data directly from this partition. Max file on FAT32 size is about 4G.

Make sure that you have the same uid on both sides of the fence otherwise you may not be able to browse your osx files except as root.

---

### Post by NickK1066 on 2007-02-25
I've been looking at this more and it seems that using a small (~4GB) HFS+ partition without journaling on could be the way to go. I've read larger linux HFS+ partitions have resulted in corruption - even with relatively recent kernels. 
Alternatively using two syncs from an SVN repository (ok if I'm at home as the fileserver could house this) or last resort a 4GB USB device.

Thanks,
Nick.

---

### Post by cocoia on 2007-02-26
> **NickK1066 said:**
> I've been looking at this more and it seems that using a small (~4GB) HFS+ partition without journaling on could be the way to go. I've read larger linux HFS+ partitions have resulted in corruption - even with relatively recent kernels. 
Alternatively using two syncs from an SVN repository (ok if I'm at home as the fileserver could house this) or last resort a 4GB USB device.

Thanks,
Nick.

Let me know how this works out, because I am interested in doing this as well. Currently using FAT, but really, really hope to switch to ZFS by Leopard.

---

### Post by oskarloko on 2007-03-02
An ext3 driver for MacOsX
[http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/")

For windows
[http://www.chrysocome.net/explore2fs]("http://www.chrysocome.net/explore2fs")
Or this
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by ouilsen on 2007-03-02
The ext3 driver on OS X is not an option for a stable environment! I use it and it makes my OS X system very unstable. I get random kernel panics but only if an ext2 drive is mounted. 

The kernel panic log that pops up after a reboot clearly identifies this driver as the cause of the crash.

Until now the driver has not resulted in any corrupted drives, though I have to fsck the ext2 drives quite often.

---

