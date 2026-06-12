---
title: "Help: Bad disk or disk drive issue"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by aseemmehta on 2008-03-23
I'm trying to install ubuntu (7.10) on my IBM-PC (512 Mb RAM, pentium) in the dual boot mode.  The download of ubuntu was good (I checked MDSUM) and enough of the operating system has been burned on the CD to allow ubuntu to boot up from the live CD (I'm posting this from ubuntu.)

However, installation to the HD has failed twice (either due to bad burn or due to a flaky CD-ROM.)  I was installing guided using 'freed space.'  I cannot start up XP anymore (I can see the BIOS and, sometimes, boot up ubuntu using the live CD.)

Anything I can do to allow the PC to be rebooted with XP?

Thanks.

---

### Post by overdrank on 2008-03-23
> **aseemmehta said:**
> I'm trying to install ubuntu (7.10) on my IBM-PC (512 Mb RAM, pentium) in the dual boot mode.  The download of ubuntu was good (I checked MDSUM) and enough of the operating system has been burned on the CD to allow ubuntu to boot up from the live CD (I'm posting this from ubuntu.)

However, installation to the HD has failed twice (either due to bad burn or due to a flaky CD-ROM.)  I was installing guided using 'freed space.'  I cannot start up XP anymore (I can see the BIOS and, sometimes, boot up ubuntu using the live CD.)

Anything I can do to allow the PC to be rebooted with XP?

Thanks.

Hi and welcome, you may try and restore the MBR
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR)
Also you may try the alternate cd to complete the installation as it is a text based installer
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by aseemmehta on 2008-03-23
Thanks for your suggestion.  I tried to fix the MBR using this method on this thread: ([http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)) but to no luck.  Going back to 'sudo dd ...' etc now.

---

### Post by logos34 on 2008-03-23
> **aseemmehta said:**
> Thanks for your suggestion.  I tried to fix the MBR using this method on this thread: ([http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)) but to no luck.  Going back to 'sudo dd ...' etc now.

Hmm, didn't know you could do that...Never heard of 'ms-sys' pkg. 

If you can find a way to restore windows boot (if you can get your hands on a XP install cd you can boot into the recovery console and do** fixmbr**, or else download the Super Grub Disk), you could try[ this installation method]("https://wiki.ubuntu.com/Installation/FromWindows") straight from the hard drive (-->'CD image approach'), bypassing your cdrom problems.

---

### Post by aseemmehta on 2008-03-23
This is what fdisk says:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3934    31599823+   7  HPFS/NTFS
/dev/sda2            9230        9730     4024282+  12  Compaq diagnostics
/dev/sda3            3935        6440    20129445   83  Linux
/dev/sda4            6441        9229    22402642+   5  Extended
/dev/sda5            9042        9229     1510078+  82  Linux swap / Solaris
/dev/sda6   *        6441        8927    19976764+  83  Linux
/dev/sda7            8928        9041      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by logos34 on 2008-03-23
You can try Super Grub Disc or an XP install CD to fix windows mbr.

---

