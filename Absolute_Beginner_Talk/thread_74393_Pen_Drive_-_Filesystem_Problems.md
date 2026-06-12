---
title: "Pen Drive - Filesystem Problems"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by duminas on 2005-10-11
The relevant line in my fstab file is:
```
/dev/sda1       /media/flash    auto    rw,user,noauto  0       0
```Now, I issue mount /dev/sda1, and then I open Nautilus and run on over to /media/flash (which I created).

Problem is, it sees my old folder, but I can't do anything to it.
I rename it, and the folder vanishes. I try to create something with the same name, and I get this lovely error:
> The name "oc_cmptr110" is already used in this folder. Please use a different name.Nautilus shows /media/flash as having no contents now, as well. If I try to rename a .html file on the pen, it just makes the thing invisible. ls can't see it, nor can Nautilus, which reports it as not even existing.

This is incredibly aggrivating when the pen is *supposed* to work on Linux fine. It's a Crucial. The **dmesg** output related to it is as follows:
> SCSI device sda: 505856 512-byte hdwr sectors (259 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 505856 512-byte hdwr sectors (259 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
VFS: Can't find ext3 filesystem on dev sda.
autofs: called with bogus options
Any help, guys?

---

### Post by Ampersand on 2005-10-11
Try commenting out the line in fstab, I've found that most usb storage media tends to be detected by gnome volume manager and mounted automatically.

---

### Post by duminas on 2005-10-11
I do not believe *gnome-volume-manager* is running at present.
I run under Fluxbox--no Gnome interface at all, nor any interaction with GDM.

Also, when I plugged it in, the device was not automounted nor made available automagically.

Also, greping for that process returns nothing.
```
0 ###### duminas ~/.fluxbox $ ps -ef|grep gnome-volume-manager
duminas  13047 10973  0 14:20 pts/0    00:00:00 grep gnome-volume-manager
```If I understand that correctly, that simply means I'm searching for it--it's not running. If I grep for gnome alone, I get this:
```
0 ###### duminas ~/.fluxbox $ ps -ef|grep gnome
duminas  10931 10876  0 07:35 tty1     00:00:03 gnome-settings-daemon
duminas  12891     1  0 13:00 ?        00:00:00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=24
```

Any idea? ^^

---

### Post by Ampersand on 2005-10-11
try 
```
 sudo mount -t vfat /dev/sda1 /media/flash 
```

I've found that usb drives sometimes don't work with auto...

---

### Post by duminas on 2005-10-11
If I do that, I can't do anything to that directory as my standard user.
Also, doing "cp" on the folder there (oc_cmptr) results in a failure of
> cp: omitting directory `/media/flash/oc_cmptr'Doing a "mv" works fine, though. Needs su privileges, however.

If I change auto to vfat in the fstab file, and then do the usual mount /dev/sda1, it works fine for my regular user.

Still kinda sucks that it nuked my files. Any way to get 'em back? T_T
Also, can I just umount it and then unplug the device, or do I need to do something else to "Safely" remove it?

Thanks~

---

### Post by Ampersand on 2005-10-11
Shouldn't be any problems unplugging after unmounting. Not sure about the missing files.

---

