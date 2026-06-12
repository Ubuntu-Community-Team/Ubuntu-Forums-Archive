---
title: "I can't get mol to boot OS X, could use some help"
date: 2006-09-12
forum: Apple PPC Users
---

### Post by beowulf62381 on 2006-09-12
Disclaimer: I have read/search so if this has been answerd it is because I over   looked the not because i did not try:-D 

OK I'm trying to get 10.4 running on Dapper using mol-0.9.17_pre9

when I type startmol --osx

Mac-on-Linux 0.9.71-pre9 [Sep 12 2006 01:56]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Running in PowerPC 7400 mode, 96 MB RAM
Timebase: 41.65 MHz, Bus: 166.63 MHz, Clock: 999 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/local/mol/x11.kbd'
Fullscreen video on VT 8.
Could not open '/var/local/mol/console.kbd'
Video driver(s): [xvideo] [console_video]

     640* 480, depth 8,32   { 0.0 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,15,32   { 60.0, 70.0, 75.0 } Hz
    1152* 864, depth 8,15,32   { 59.9 } Hz
    1280* 854, depth 8,15,32   { 60.0 } Hz
    1280*1024, depth 8,15,32   { 60.0, 60.0 } Hz
    1440* 960, depth 8,32   { 0.0 } Hz
    1600*1024, depth 8,32   { 0.0 } Hz
    1680*1050, depth 8,15,32   { 0.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

DHCP nameserver exported: 68.105.161.20
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Ethernet Interface 'tun-<tun0>' @ 00:00:0D:EA:DB:EE

    ip/mask: 192.168.41.2/255.255.255.0  gw: 192.168.41.1
    broadcast: 192.168.41.255  nameserver: 192.168.41.1

ALSA sound driver (device 'default')
ALSA: failed to setup mixer

    CD    /dev/cdrom       CD/DVD         <read-only>   ------
    HFS   /dev/hda2        bootstrap      <rw>  512 MB
    Unembedded HFS+ /dev/hda4                       <rw> 10112 MB

SCSI devices:

    SCSI  /dev/cdrom       [CDROM/DVD driver]


>> ==================================================
>> MacOS X Boot Loader 0.9.70 [96MB memory map patch]
>> Candidate boot volume: /mol-blk@0/disk@0:0
>> /mol-blk@0/disk@0:0,\mach_kernel (4313028 bytes)
>> /mol-blk@0/disk@0:0,\System\Library\Extensions.mkext
>> ==================================================

<*> IRQ vectorCanBeShared 3
<*> IRQ vectorCanBeShared 4
<*> IRQ vectorCanBeShared 2
<*> Block Driver v1.1
<*> SCSI driver v1.03
<*> IRQ vectorCanBeShared 6
<*> IRQ vectorCanBeShared 24
ablk iofunc: Bad address
ABlk engine error

the penguin hugs the apple the spinny at the bottom spins and that's it. when i close that window,

***** SIGNAL 13 [Broken pipe] in thread main-thread *****
X connection to :0.0 broken (explicit kill or server shutdown).
cleaning up...
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Terminating threads...
DONE

shows up in the original terminal window](*,)  any help would be appreciated

---

### Post by ubuntubrian on 2006-09-15
it takes several minutes for my OS X to boot up with MOL. The apple hugging tux sits there for quite a while, maybe 4-5 minutes,before OS X starts and presents a log-in screen.

---

### Post by jave on 2006-09-15
I'm definitely no expert, but try changing the amount of memory that MOL uses in the file /etc/mol/molrc.osx.  The HOWTO link listed below suggests at least 128MB.

[https://help.ubuntu.com/community/MacOnLinuxHowto](https://help.ubuntu.com/community/MacOnLinuxHowto)

Hope this helps....

---

