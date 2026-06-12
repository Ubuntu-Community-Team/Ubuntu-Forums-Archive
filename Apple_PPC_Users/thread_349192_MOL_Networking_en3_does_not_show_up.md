---
title: "MOL Networking: en3 does not show up"
date: 2007-01-29
forum: Apple PPC Users
---

### Post by luispedro on 2007-01-29
Hello,

I have followed [http://www.ubuntu.com/wiki/MacOnLinuxHowto](http://www.ubuntu.com/wiki/MacOnLinuxHowto) and looked at other sites.

However, I do not get a "en3" network port on the mac side.

I'm using Mac OS X 10.3.9

Any ideas?

Here's the output of startmol -X:

»»»»»»»»»»»»»»» START «««««««««««««««««
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 7400 mode, 512 MB RAM
Timebase: 18.43 MHz, Bus: 73.72 MHz, Clock: 666 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
Video driver(s): [xvideo]

     640* 480, depth 8,32   { 0.0 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,32   { 0.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

No video mode match the default one.
DHCP nameserver exported: 192.168.1.1
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Ethernet Interface 'tun-<tun0>' @ 00:00:0D:EA:DB:EE
ALSA sound driver (device 'default')
MOL SCSI controller registered


    <No SCSI Devices>

    Unembedded HFS+ /dev/hda3                       <rw> 18945 MB BOOT
    CD   /dev/cdrom       CD-ROM         <read-only>   ------
----> /dev/hda2 might be a boot-strap partition.
------> The volume '/dev/hda3' is locked
------> /dev/hda4 is linux-mounted with write privileges.
Could not open '/dev/hda4' with read-write permissions
No volumes found in '/dev/hda'
No volumes found in '/dev/hdb'
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'


>> ==================================================
>> MacOS X Boot Loader 0.9.70
>> Candidate boot volume: /mol-blk@0/disk@1:0
>> /mol-blk@0/disk@1:0,\mach_kernel (3872560 bytes)
>> /mol-blk@0/disk@1:0,\System\Library\Extensions.mkext
>> ==================================================

<*> MOL acceleration for 10.3
<*> Block Driver v1.1
Mounting MOL driver disk
+ Video Driver v1.12
cleaning up...
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Terminating threads...
DONE
»»»»»»»»»»»»»»»»»»»» END «««««««««««««««««««««««««««««««««««

---

### Post by linear on 2007-01-30
Do you get an "en2" or anything else? If so, just use that.

---

### Post by luispedro on 2007-01-30
No, I get nothing at all.

---

### Post by luispedro on 2007-01-30
GOT IT!!!

I had missed that you're supposed to install some drivers while **inside** MOL.

working now.

---

