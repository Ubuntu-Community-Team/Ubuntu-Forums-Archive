---
title: "No Longer can see drives !"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-12-03
Here's my fstab, but I no longer see the files in mnt/C,E,F !!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=f9c9c756-b635-4527-99fc-7701a1e6c847 /               ext3    defaults,erro$
/dev/hdb3        /mnt/Data      ext3    nodev,nosuid    0       2
# /dev/hdb5
UUID=102024b5-03fd-47eb-882f-e60afce29cc7 none            swap    sw           $
/dev/hda1       /mnt/C          ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda5       /mnt/E          ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda7       /mnt/F          ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by Scheater5 on 2006-12-03
If I understand your problem correctly, I've had similar problems - but ususally only when I try and access drives from multiple OS's.  Eventually I can only access drives from one OS - I've had this problem with USB drives, and it completely killed Windows in a dual-boot I set up for a friend.  I haven't found a solution - but could your problem be related to accessing drives in multiple OS's, or perhaps even multiple installs of the same OS?

---

### Post by taurus on 2006-12-03
```
sudo mount -a
df -h
```

---

### Post by Drakkor on 2006-12-03
Yeah,it's windows partitions,and they had a nasty shutdown,as witnessed here,going to try to boot to windows and shutdown,properly,lol :mad:

drakkor@Ubuntu-Edgy:~$ sudo mount -a
Password:
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
Failed to mount '/dev/hda5': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
Failed to mount '/dev/hda7': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
drakkor@Ubuntu-Edgy:~$

---

### Post by Drakkor on 2006-12-03
Hmmmmmmmmmm................. seems a proper reboot does wonders,lol :p 
All is well !!

---

