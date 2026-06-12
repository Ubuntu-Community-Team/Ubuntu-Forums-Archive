---
title: "Linux inside Linux"
date: 2007-01-20
forum: Apple PPC Users
---

### Post by Uta on 2007-01-20
I am currently using a very stable Dapper install that has "Mac on Linux" working great, even with wireless. What I would like to do now is install a different ppc linux distro on an additional internal HD and run that from my primary linux (Dapper) just like I do with Mac OSX via mol. 
Is MOL able to do this or is there another application I need to install? Thanks!

---

### Post by dpny on 2007-01-20
According to the MOL website, you can run Linux from within MOL. I believe the command to start is something like startmol --linux. However, I haven't done it so I  have no details.

---

### Post by Uta on 2007-01-20
I couldn't find any documentation on linux in linux on the mol site, Where did you find it exactly?
On the mailing list for mol, I did find some info.

---------------------------------------

shell prompt if one does something like

startmol --linux=/tmp/vmlinuz

with the following lines in /etc/molrc:

linux_initrd: /tmp/ramdisk.image.gz
linux_cmdline: 'ramdisk_size=10000 boot=/dev/ram0 init=/bin/sh'

It should work with any 2.2 or 2.4 kernel. The video mode must be set to depth 32 though.
-------------------------------------
My new project!
thanks--

---

### Post by dpny on 2007-01-20
Typing ```
startmol --help
```

gives, among other things:

```
Client OS Selection:
       --test          run self-test and exit
       --newworld      Boot Mac OS (classic) the "newworld" way [default]
       --oldworld      Boot Mac OS (classic) the "oldworld" way
  -X,  --osx           Boot Mac OS X
       --linux         Boot Linux
       --elf=image     run statically linked ELF-image inside MOL
```

---

### Post by Uta on 2007-01-21
If you know how to boot linux with mol please tell me.
My second linux distro is on a secondary IDE drive "hdb5" it's an install of xubuntu.
My primary drive that has mol is hda5. MOL boots osx perfectly. When I first installed mol it placed an install package on my osx desktop which i installed. 
Is there something I need to install on my 2nd linux distro for mol to use?
What would the boot parameters be?
If I just run "startmol --linux"
I get this:

> Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 3
Running in PowerPC 7400 mode, 64 MB RAM
Timebase: 24.90 MHz, Bus: 99.63 MHz, Clock: 1200 MHz
-----> /BK/yaboot-1.3.7/second/yaboot: No such file or directory
-----> /BK/linux-mol/vmlinux: No such file or directory
-----> /BK/initrd: No such file or directory
Using USB mouse on /dev/input/mice
Could not open '/var/lib/mol/x11.kbd'
Fullscreen video on VT 9.
Could not open '/var/lib/mol/console.kbd'
Cache enabled for console-video
Video driver(s): [xvideo] [console_video] 

     640* 480, depth 8,32   { 0.0 } Hz
     800* 600, depth 8,32   { 0.0 } Hz
    1024* 768, depth 8,32   { 0.0 } Hz
    1152* 864, depth 8,32   { 0.0 } Hz
    1280*1024, depth 8,15,32   { 0.0, 60.0 } Hz
    1600*1200, depth 8,32   { 0.0 } Hz

HACK: Mapping framebuffer to 81000000
DHCP nameserver exported: 192.168.0.1
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Ethernet Interface 'tun-<tun3>' @ 00:00:0D:EA:DB:EE
Failed to register sound card

----> (disk_open) Opening /BK/debian: No such file or directory


>> =============================================================
>> Mac-on-Linux OpenFirmware 0.9.70
>> prom_change_phandle returned an error
>> *** Boot failure! No secondary bootloader specified ***
cleaning up...
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Terminating threads...
DONE

I need to set a secondary bootloader. Is that the bootloader on hdb5? My mac osx partition does not need to be mounted in order for mol to use it, does this apply to linux also?

---

### Post by Uta on 2007-01-21
I heard back from a developer of mol and the answer is no linux inside linux.

> Right now, it's not possible to boot 2.6 kernels and *very* 
difficult to boot 2.4 kernels.  I'm currently working on creating a 
platform that would allow booting 2.6 kernels, but it's still in 
progress.  I will announce when it's working both on the Sourceforge 
page and on the MOL mailing list.

It is in works though. :)

So my next question is what software that runs on ppc linux, will run linux inside linux?

---

