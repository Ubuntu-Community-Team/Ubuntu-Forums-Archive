---
title: "Fdisk and Disk Utility Discrepencies"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by joshgtv6 on 2006-10-26
Hello again everyone, after getting my second drive mounted I was wondering if someone could give me some help with something I can't figure out.  And I took screenshots so you all don't think i'm crazy or something.  

I was having issues with a drive insisting it was formatted to NTFS even though it wasn't.  So i installed a fresh copy of Ubuntu to it to make sure that is was in fact formatted as EXT3.  However, the disk utility is still claiming it's NTFS, and FDISK says it's EXT3. So formatted it again to EXT3 and then rebooted and got a GRUB 15 error so i just reinstalled GRUB from the LIVE CD and fixed that little issue.   

[IMG]http://h1.ripway.com/jpeifley/Screenshot-1.png[/IMG]
[IMG]http://h1.ripway.com/jpeifley/Screenshot.png[/IMG]

What is going on here?  Is this some kind of bug?

Here is what I want to do.  I want to format this amazing drive that claims to be two different file system into an EXT3 storage disk so i can read and write to it.  Simple as that.  I'm using the 6.06 Dapper install.

---

### Post by deadgobby on 2006-10-26
Have you tried this link?
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by joshgtv6 on 2006-10-26
yeah, i've tried that.  I get a message saying that Line 9 in the fstab file is wrong when i attempt to mount when everything is done.  

  [B]GNU nano 1.3.10             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /dev/hdb1 /storage ext3 defaults 0 0[/B]

[I]jpeifley@jpeifley-desktop:~$ sudo mount -a
[mntent]: line 9 in /etc/fstab is bad
jpeifley@jpeifley-desktop:~$
[/I]

This is my fdisk -l readout:

[B]Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4770    38314993+  83  Linux
/dev/hda2            4771        4863      747022+   5  Extended
/dev/hda5            4771        4863      746991   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       35345   283908681   83  Linux
/dev/hdb2           35346       36481     9124920    5  Extended
/dev/hdb5           35346       36481     9124888+  82  Linux swap / Solaris
[/B]

---

