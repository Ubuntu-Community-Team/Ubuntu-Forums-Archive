---
title: "Strange Booting Errors"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-08-09
When I try booting Ubuntu, about one in ten boots, when it should get to the login screen, shows these errors:

```
[  140.79XXXX] sus: 2:0:0:0: rejecting I/O to dead device
[  140.79XXXX] EXT3-fs error (device sde3): ext3_find_entry: reading directory # XXXXXX offset 0
```

It repeats that a few times, and the X's are different numbers each time.  Then the screen sat there for a few minutes, but then it suddenly showed this error about 15 times:

```
/etc/init.d/rc: 2: sed: not found
```

Finally, it gave me these errors:

```
init: unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (4085) terminated with status 255
```

Then nothing else comes up on the screen.  I have to turn off the computer manually, but then when I try booting again, everything is fine.  Should I be concerned about the errors?

Thanks.

---

### Post by splintercellguy on 2007-08-09
The first message concerns me. Perhaps you are having power issues or loose cables in your comp?

---

### Post by Yes on 2007-08-09
No power issues.  Where would the cables be?  Anywhere in and around the computer?

Thanks.

---

### Post by splintercellguy on 2007-08-09
The cables that hook up to your hard drive.

---

### Post by duydaniel on 2007-08-09
> **Yes said:**
> No power issues.  Where would the cables be?  Anywhere in and around the computer?

Thanks.

I believe splintercellguy meant you open up the comp case or tower (whatever you call it) and secure all the cable connections in your comp, especially the hard drive one. Try to plug out and in again... all the connector...

[edit] already replied

---

### Post by Yes on 2007-08-10
Well, I never get any kind of errors like this in Windows that might suggest that the problem is lying in the cables going into the computer.  Ubuntu is installed on an external hard drive, and there's only two cables going out of it.  One seems lose, but it's pushed in as far as it can go.  Is there anything else that might be causing the problem?

Thanks.

---

### Post by Yes on 2007-08-11
Bump.

---

### Post by Yes on 2007-08-11
Bump.

---

### Post by Yes on 2007-08-12
Bump.

---

### Post by Arthur Archnix on 2007-08-13
You do tend to bump too much Yes. Is it possible to edit your message, and append a bump to the end of the last one that has not received a reply? I haven't tried that, but see if that does the same things as posting a new empty bump message. Or better still, post a message that let's us now what else you've tried in the last 16 hours.

I suspect it's a cable. You said it doesn't happen in windows. Are windows and ubuntu on the same external hard-drive? If not, then the only way to rule out cable is to try a different cable. 

It could be some other problem though, most likely with how it's getting mounted. Post the output of "mount", your fstab file, and a fdisk -l
```
mount
sudo gedit /etc/fstab
sudo fdisk -l
```
Is this problem new, or has it always been happening?

---

### Post by Yes on 2007-08-13
mount:

```
/dev/sdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /boot type ext3 (rw)
/dev/sdb4 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=username)
```

sudo gedit /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=2c9f0a42-ef79-48a5-a048-d7bbf4588fe5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=bd310f8d-2341-41a6-ad01-bd8ec558d581 /boot           ext3    defaults        0       2
# /dev/sdb4
UUID=52c94247-d6e8-4127-bf63-93f937c3fc80 /home           ext3    defaults        0       2
# /dev/sda1
UUID=7C70470E7046CF18 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=13775493-0c0a-4670-87e0-3634ae9c504d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

sudo fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96358+  83  Linux
/dev/sdb2           19263       19457     1566337+  82  Linux swap / Solaris
/dev/sdb3           18335       19262     7454160   83  Linux
/dev/sdb4              13       18334   147171465   83  Linux

Partition table entries are not in disk order
```

This is not new, although I'm not sure if this has always been happening.

Thanks.

---

### Post by Arthur Archnix on 2007-08-13
Yeah, your Ubuntu install is on its own hard-drive. Take a hard look at the cable connecting to the computer, even try plugging into a different usb port if that's how you're connecting. Certainly try swapping out the cable if that's possible.

---

### Post by gwi on 2007-09-26
> **splintercellguy said:**
> The first message concerns me. Perhaps you are having power issues or loose cables in your comp?

That first message (rejecting I/O to dead device): I get it all the time, along with the following (taken from handwritten notes while watching the messages appear during boot):
```
ata2: softreset failed, port not ready
ata2: softreset failed (timeout)
ata2.00: exception Emask 0x0 sAct 0x3C SErr 0x0 action 0x2 frozen
ata2.00: exception Emask 0x0 sAct 0x47 SErr 0x0 action 0x2 frozen
ata2: hardreset failed (PHY debouncing failed)
ata2.00: exception Emask 0x0 sAct 0x0 SErr 0x40d0000 action 0x2 frozen
irq_stat 0x00060002 failed to transmit command FIS
scsi 3:0:0:0: rejecting I/O to dead device
```
Above messages are not necessarily in the order they appeared in (as I said: handtaken notes while watching the screen). Some are there one time, some are repeated dozens of times.

Trying to solve the problem I tried:[LIST]
[*]three different motherboards (Asus A8N, Abit KN9, Asus M2N32);
[*]three different processors (Athlon64 3200+, Opteron165, AthlonX2 4800+);
[*]three different chipsets (nForce4, nForce570, nForce590);
[*]four different SATA controlers (in the chipsets mentioned above, and a SiI3124);
[*]two different SATA harddisks (Seagate Barracuda 7200.9, Western Digital WD5000AAKS);
[*]several cables and ports on the controllers.
[/LIST]
So far after every reinstall the system runs stable, but after a few weeks the problems start, at a rapidly increasing frequency. I use my computer for a few hours almost every day, and shutdown after use.

I have one SATA harddisk and one ATAPI DVDRW drive, so no raid, no SCSI, no ATA.
Right now, the system freezes before I can login, so forget about collecting logs.

Would be nice to see this problem solved. I is really starting to piss me off (and thinking "how would Vista do?"). The last four months I've spent more time trying to get my system running, than doing real work on it.

---

