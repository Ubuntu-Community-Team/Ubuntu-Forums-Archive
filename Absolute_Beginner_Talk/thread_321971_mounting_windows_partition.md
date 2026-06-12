---
title: "mounting windows partition"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by uthturn on 2006-12-19
ok so i had this working where both partitions showed on my desktop but when i came home and booted up they were gone. heres my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=9c9d2a46-4637-4d32-92f7-3122a0459375 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1e0a7d37-3d3a-41d8-a0e1-96445746e92c none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/hdb1    /media/media    ntfs-3g    defaults,locale=en_US.utf8    0    0
thanks for ANY help!

---

### Post by taurus on 2006-12-19
What's the output of this command from a terminal then?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by uthturn on 2006-12-19
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              41G  2.0G   37G   6% /
varrun                347M   84K  347M   1% /var/run
varlock               347M     0  347M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                347M     0  347M   0% /dev/shm
lrm                   347M   18M  330M   5% /lib/modules/2.6.17-10-generic/volatile
/dev/hdd              481M  481M     0 100% /media/cdrom0
:)

---

### Post by taurus on 2006-12-19
What happens when you run this command at the prompt?

```
sudo mount -a
```

---

### Post by uthturn on 2006-12-19
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.

---

### Post by uthturn on 2006-12-19
thanks for the help i'll try these

---

### Post by taurus on 2006-12-19
I take it /dev/hda1 is your XP and somehow it is not clean!!!  You need to boot into XP and defrag or scan it to fix whatever the problem it is having...

Otherwise, what happens if you mount it by hand?

```
/dev/hda1  /media/windows  ntfs  nls=utf8,umask=0222  0  0
```

---

### Post by uthturn on 2006-12-19
apparently i did not log off properly. i just had to reboot windows than exit properly thanks for all your help

---

