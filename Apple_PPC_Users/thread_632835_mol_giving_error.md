---
title: "mol giving error???"
date: 2007-12-05
forum: Apple PPC Users
---

### Post by sunnyhanda on 2007-12-05
I have just install MOL in my imac g3 running ubuntu feisty then i try to install mac os 9 on it and it works fine but later when i tried OS X 10.3 on it it gives following error- please have look and help thanks.
[B]
root@imac-apple:~# startmol -X
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 750 mode, 512 MB RAM
Timebase: 24.96 MHz, Bus: 99.86 MHz, Clock: 450 MHz
-----> drivers/mods1.mkext: No such file or directory
-----> drivers/mods2.mkext: No such file or directory
Using USB mouse on /dev/input/mice
OHCI USB controller registered 
Could not open '/var/lib/mol/x11.kbd'
Could not open driver 'drivers/video.x': No such file or directory
Fullscreen video on VT 9.
Could not open '/var/lib/mol/console.kbd'
Video driver(s): [xvideo] [console_video] 

     640* 480, depth 8,32   { 116.6 } Hz
     800* 600, depth 8   { 56.2, 94.8 } Hz
     800* 600, depth 8,15,32   { 99.9 } Hz
    1024* 768, depth 8,15,32   { 0.0 } Hz
    1024* 768, depth 8   { 74.8 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,15,32   { 60.0, 60.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

ALSA sound driver (device 'default')
ALSA: failed to setup mixer
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------ 
----> /dev/hda2 might be a boot-strap partition.
------> /dev/hda3 is linux-mounted with write privileges.
Could not open '/dev/hda3' with read-write permissions
No volumes found in '/dev/hda'
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


Can't read Elf32 image header
Fatal error: drivers/bootx is not an ELF image

cleaning up...
Terminating threads...
DONE[/B]

---

### Post by stmiller on 2007-12-06
That MOL version is two years old, as you can see by the 2005 date. I never got OS X to boot with that Ubuntu supplied version. Fetch the latest directly from the mol website and try that.

---

