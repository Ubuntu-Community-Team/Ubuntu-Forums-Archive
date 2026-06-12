---
title: "mount: I could not determine the filesystem type, and none was specified"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by oiler on 2007-04-13
absolute new user running Xubuntu 6.06.  when trying to mount floppy below message returned.  Thought auto in fstab took care of file type.:o solutions?

Oiler




Via C3 

cafe@cafe-desktop:~$ mount /media/floppy0
mount: I could not determine the filesystem type, and none was specified

um# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

cafe@cafe-desktop:~$ ls /media
cdrom  cdrom0  floppy0

cafe@cafe-desktop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

---

### Post by taurus on 2007-04-13
Try something like

```
sudo mount -t vfat /dev/fd0 /media/floppy0
```

---

### Post by oiler on 2007-04-13
Taurus,

thanks-that does successfully mount in terminal mode and files can be seen and opened in \media\floppy0 folder.  what am i missing here?  is this only way to mount and unmount in this distro?

---

### Post by arpad on 2008-03-26
I'm going to resurrect this thread since I ran into the same problem and the same lack of explanation/solution.

I created some floppies for use with my floppyfw firewall/router. They're DOS format and dealing with the floppies has been an exercise in frustration.

I don't mind having to type in commands at the command line but there's Nautilus which sometimes mounts/unmounts my floppies, sometimes doesn't. Is there some way to get to the bottom of this?

---

