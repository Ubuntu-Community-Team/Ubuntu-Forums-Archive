---
title: "Want to install Ubuntu"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by NightmareFH on 2007-02-01
I have an external 80gb WD HDD.  I want to install Ubuntu to this external HDD and at the same time keep my Windows installation on my internal HDD.  Is there any special formatting/partitioning I need to do to my external HDD in order to install my Ubuntu distro?

---

### Post by BrownieMan on 2007-02-01
I think a much easier way of doing things would be to just install Ubuntu on your internal hardrive alogn with Windows. You can dual boot, which is basicaly doen automaticaly for you when you install Ubuntu. Installing an OS on an external hardrive is areally bad ide ain general. Externals can't transfer data as fast and as much as internal ones. This is because most external ones use a USB or some other device.

---

### Post by beaulanger on 2007-02-01
sorry

---

### Post by Tiburon41 on 2007-02-01
I'll give you my idea:

To preface, I have Partition Magic (IMHO an outstanding utility) and used it to it's fullest.

I have an 80GB HDD that is my master (with Windows XP Pro), partitioned into a Windows XP (C:) partition, a Programs (D:) partition, and a Music (E:) partition.

I also have a 160GB slave HDD that I originally purchased for video editing.  On this, I have a Media (F:) partition, and an Other Stuff (G:) partition.  All partitions on BOTH drives are FAT32 file system.

I used Partition Magic (because FDISK, etc scare the hell out of me) and moved/re-sized the two partitions on my slave drive to leave me with about 30GB of free, unallocated, unformatted space.  I installed Ubuntu to this space, and installed GRUB to a floppy, creating a dual boot system, without disturbing the MBR on my Windows drive, and Windows doesn't even know Ubuntu is there.  I can boot into either OS at will, and I even ran the drivemounter script so I can access all my Windows files from within Ubuntu.

YMMV.

---

### Post by jd65pl on 2007-02-01
See [here]("http://gparted.sourceforge.net/livecd.php") for an open source alternative to partition magic.

---

