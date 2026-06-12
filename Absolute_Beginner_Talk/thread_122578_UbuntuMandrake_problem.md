---
title: "Ubuntu/Mandrake problem"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by writerthesp77 on 2006-01-28
Greetings all,

I'm a Linux newbie.  I bought Mandrake 10 Discovery last year and installed it on an older PC.  I got my Ubuntu discs in the mail yesterday and installed it on the same machine.

Before installing, the hard disk had three partitions:

hda1 - 6.4GB, bootable (where Mandrake installed itself)
swap - 528MB
hda6 - 12.5GB (all empty)

I repartitioned hda6 into two partitions:

hda6 - 6.5 MB, bootable (where I installed Ubuntu)
hda7 - 6.0 MB (all empty)

Thus far, pretty much all has gone well with Ubuntu.  I have two issues, though.

1.  When I log into Ubuntu, I have icons for hda1 and hda6.  I can browse them, but I can't write to them.  How do I change this?

2.  I can't log into Mandrake now.  When I attempt to sign in, I get an error message saying that KDE doesn't have access to "$home".

Can anybody help?

---

### Post by steve.horsley on 2006-01-28
[QUOTE=writerthesp77]
I repartitioned hda6 into two partitions:

hda6 - 6.5 MB, bootable (where I installed Ubuntu)
hda7 - 6.0 MB (all empty)

Thus far, pretty much all has gone well with Ubuntu.  I have two issues, though.

1.  When I log into Ubuntu, I have icons for hda1 and hda6.  I can browse them, but I can't write to them.  How do I change this?

2.  I can't log into Mandrake now.  When I attempt to sign in, I get an error message saying that KDE doesn't have access to "$home".

Can anybody help?[/QUOTE]

There is something wrong here. If Ubuntu is installed on hda6, then it shouldn't be making an hda6 icon. Can you post the contents of /etc/fstab, and also the output from these commands:
fdisk -l
mount

Steve

---

### Post by writerthesp77 on 2006-01-28
Steve, thank you very much for your help.  I'm posting fstab, fdisk and mount in that order.  Let me also say that when I typed fdisk -l, I got no output.  A friend of mine told me to enter "sudo fdisk -l" and that's the output posted below.  Thanks again.

----

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0





Disk /dev/hda: 19.2 GB, 19259154432 bytes
16 heads, 63 sectors/track, 37317 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12190     6143728+  83  Linux
/dev/hda2           12191       24831     6370935+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/hda3           24847       37310     6281415   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           12191       13205      511528+  82  Linux swap / Solaris
/dev/hda6           13206       24831     5859375   83  Linux





/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type ext3 (rw)
/dev/hda6 on /media/hda6 type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

---

### Post by writerthesp77 on 2006-03-31
bump

---

