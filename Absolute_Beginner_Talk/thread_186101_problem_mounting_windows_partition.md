---
title: "problem mounting windows partition"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Kleist on 2006-06-01
I'd appreciate any help.

I just installed ubuntu in my computer. I left one partition with my documents and music, and in the free space I installed ubuntu. Now, I want to mount the ntfs partition, but nothing happens.

My original fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Then, I insert the last line and I delete the line which starts with /dev/hda6, since this is the partition I want to mount:


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda6 /media/windows ntfs umask=0222 0 0

After this I boot the computer but the partition is not mounted.
I tried to do it manually with:

sudo mount /dev/hda6 /media/windows/ -t ntfs -o umask=0222

and I get this:

mount: wrong fs type, bad option, bad superblock on /dev/hda6,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


[4294764.526000] Bluetooth: HCI device and connection manager initialized
[4294764.526000] Bluetooth: HCI socket layer initialized
[4294764.604000] Bluetooth: L2CAP ver 2.7
[4294764.604000] Bluetooth: L2CAP socket layer initialized
[4294764.685000] Bluetooth: RFCOMM ver 1.5
[4294764.685000] Bluetooth: RFCOMM socket layer initialized
[4294764.685000] Bluetooth: RFCOMM TTY layer initialized
[4295274.341000] NTFS-fs error (device hda6): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4295274.341000] NTFS-fs error (device hda6): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4295274.341000] NTFS-fs error (device hda6): ntfs_fill_super(): Not an NTFS volume.


What am I doing wrong? Any help, I'll appreciated.

---

### Post by jorn on 2006-06-01
Take alook at this:
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)
It's for an old distro, but it should work.

---

### Post by catlett on 2006-06-01
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Kleist on 2006-06-01
Thank you very much. I could do it!

---

### Post by catlett on 2006-06-01
Now if you want to do it the other way i.e. access ubuntu's partition in windows, go to my signature and hit on the link after "drivers to access ext2/3 partitions"

---

### Post by Boelcke on 2006-06-04
I've been struggling mounting both a FAT32 partition, and some NTFS partitions in Ubuntu.  This script is like butter:

[http://www.ubuntulinux.nl/files/diskmounter](http://www.ubuntulinux.nl/files/diskmounter)

It checks out what's available, and updates your fstab file for you!  If you're interested, it's a good idea to check out that /etc/fstab file afterwards to see how it did it.  Otherwise, it just worked for me!

---

