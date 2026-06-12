---
title: "&quot;?dev/sdb2 not found or not a block device.&quot;"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-01-31
Hello Everyone
i did a clean install of ubuntu by deleting my previous windows vista partition.

I got error 17 when I rebooted without the cd from grub and i looked around a few threads and followed their advises:

my ext3 extension is /dev/sdb2 by the way (i have no idea what that means)

mkdir /mnt/root
mount /dev/xxx? /mnt/root
chroot /mnt/root /bin/bash
grub-install /dev/xxx

Everything went well except for the last line, it returns: /dev/sdb2: not found or not a block device...

I attempted this command
cat /etc/fstab

and i got this
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=23262e0e-2291-488c-95cb-3c6f5ab556c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1266AFEC66AFCF33 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=80C2F69090FA0800 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=000EE7970EE7844E /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=1ecd7755-3886-45b7-b0ae-97d7ba3bf5a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
"



What should i do if I want to be able to boot into my ubuntu partition under normal conditions?

---

### Post by kpkeerthi on 2008-01-31
Use [super grub disk]("http://supergrub.forjamari.linex.org/") to restore GRUB

---

### Post by c0met on 2008-01-31
"/dev/sdb2" means the 2nd partition (that is, 2) on your second hard drive (that is, sdb): sda would be your first hard drive.

The SuperGRUB program that was mentioned above is good. You can also download and ISO from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

You will need to burn the ISO file to a CD and then boot from the CD. All you need to do then is to follow the prompts. While I have had some good success with this program, every now and again, it doesn't solve my problems. If that happens to you, you will need to reinstall GRUB. The below webpage has some tips for that...

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

