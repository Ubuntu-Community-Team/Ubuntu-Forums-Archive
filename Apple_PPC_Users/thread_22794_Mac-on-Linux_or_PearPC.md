---
title: "Mac-on-Linux or PearPC"
date: 2005-03-29
forum: Apple PPC Users
---

### Post by Myles3 on 2005-03-29
Hi I have fully installed linux on my G3 iBook and I want to install an Emulation of Mac OS X. What is better Mac-on-Linux or PearPC?

I am maily looking for good hardware support?

---

### Post by TravisNewman on 2005-03-30
MOL. It's amazing. Everything runs well, and pretty snappy. I've used it on a g3 imac with no issues at all. It actually gives better performance for a very few things. PearPC is full on emulation (correct me if I'm wrong) while MOL is kinda paravirtualization. It runs natively, with basically an emulation layer to interact with it.

---

### Post by Leonida on 2005-03-30
[QUOTE=Myles3]What is better Mac-on-Linux or PearPC?[/QUOTE]

Mol, see these [screenshots](http://www.freesmug.org/forums/foss.nbs/275805139923) if you have any doubts.

---

### Post by dherren on 2005-03-30
[QUOTE=panickedthumb]MOL. It's amazing. Everything runs well, and pretty snappy. I've used it on a g3 imac with no issues at all. It actually gives better performance for a very few things. PearPC is full on emulation (correct me if I'm wrong) while MOL is kinda paravirtualization. It runs natively, with basically an emulation layer to interact with it.[/QUOTE]

following the instructions in the wiki, I get snagged up when I try to do the mol package install. See:

root@voyager:/usr/src/modules/mol # debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_installdocs
dh_installmodules
dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_gencontrol
dh_md5sums
dh_builddeb --destdir=/..
dpkg-deb: building package `mol-modules-2.6.8.1-3-powerpc' in `/../mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb'.
root@voyager:/usr/src/modules/mol # cd ..
root@voyager:/usr/src/modules # ls -al
total 12
drwxr-xr-x    3 root     src          4096 2004-08-03 12:18 .
drwxrwsr-x    6 root     src          4096 2005-03-30 10:11 ..
drwxr-xr-x    8 root     src          4096 2005-03-30 10:21 mol
root@voyager:/usr/src/modules # dpkg -i /usr/src/mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb
dpkg: error processing /usr/src/mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /usr/src/mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb

The instructions say that the file name will change, but even copying the file name given during the compilation of the modules, I can't get beyond this point.

Advice?

---

### Post by Myles3 on 2005-03-30
Another thing I am scared of is my screen size 1024 by 768... will this be a problem or will i have to go higher?

---

### Post by dherren on 2005-03-31
[QUOTE=dherren]following the instructions in the wiki, I get snagged up when I try to do the mol package install. See:

[snip]

root@voyager:/usr/src/modules # dpkg -i /usr/src/mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb
dpkg: error processing /usr/src/mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /usr/src/mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb

The instructions say that the file name will change, but even copying the file name given during the compilation of the modules, I can't get beyond this point.

Advice?[/QUOTE]

OK, answered my own first question. The file:

mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb

had been created right at the root level of the linux volume. Installation proceeded just fine once I found it and proceeded with the wiki instructions. However, I've hit another snag which I'll place in a separate post below....

---

### Post by dherren on 2005-03-31
Installation completed and now when trying to boot mol, I encounter the following:

david@voyager:~ $ startmol --osx
Mac-on-Linux 0.9.70 [Aug 3 2004 16:18]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 7400 mode, 512 MB RAM
Timebase: 24.96 MHz, Bus: 99.86 MHz, Clock: 300 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Fullscreen video on VT 8.
Could not open '/var/lib/mol/console.kbd'
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,32   { 0.0 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,32   { 0.0 } Hz
    1152* 768, depth 8,15,32   { 0.0, 54.7 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

ALSA sound driver (device 'default')
ALSA: failed to setup mixer
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
    Unembedded HFS+ /dev/hda3                       <rw> 10112 MB
    Unembedded HFS+ /dev/hda5                       <rw> 41999 MB
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


>> ==================================================
>> MacOS X Boot Loader 0.9.70
>> Candidate boot volume: /mol-blk@0/disk@1:0
>> /mol-blk@0/disk@1:0,\mach_kernel (3863716 bytes)
>> /mol-blk@0/disk@1:0,\System\Library\Extensions.mkext
>> ==================================================

<*> MOL acceleration for 10.3
<*> Block Driver v1.1
Mounting MOL driver disk
+ Video Driver v1.12
ablk iofunc: Input/output error
ABlk engine error


AT this point the boot process stalls and doesn't proceed. I have already seen the tux hugging apple graphic, the mol window goes blue, the linux cursor changes to the macosx cursor, and then nothing.

This is an original Ti laptop with a 60 gig drive installed, partitioned into two OSX partitions with a third partition for ubuntu (subsequently re-partitioned by the ubuntu installer).  I wonder if the partitions are confusing the mol boot? Only one of the OSX partitions is bootable--the other is just data.

Suggestions?

---

