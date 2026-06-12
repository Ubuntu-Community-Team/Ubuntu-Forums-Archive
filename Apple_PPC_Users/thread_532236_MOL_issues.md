---
title: "MOL issues"
date: 2007-08-22
forum: Apple PPC Users
---

### Post by gamgee911 on 2007-08-22
I have installed mol and mol-drivers-macosx from synaptic and I did run molvconfig.  I am running into an issue when I try and run startmol -x.  I believe it has something to do with the fact that when I boot into Ubuntu, I have it configured so that it also mounts my mac os x partition on the desktop.  I would really to keep that configuration but if it interferes with mol then oh well.  Is the mounted partition the problem?  Here's the message I get when running sudo startmol-x

```
Mac-on-Linux 0.9.70 [Nov 20 2005 11:45]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Running in PowerPC 7400 mode, 48 MB RAM
Timebase: 33.28 MHz, Bus: 133.12 MHz, Clock: 533 MHz
Could not open driver 'drivers/misc.nw': No such file or directory
Using USB mouse on /dev/input/mice
OHCI USB controller registered 
Could not open '/var/lib/mol/x11.kbd'
Could not open driver 'drivers/video.nw': No such file or directory
Fullscreen video on VT 9.
Could not open '/var/lib/mol/console.kbd'
Cache enabled for console-video
Video driver(s): [xvideo] [console_video] 

     640* 480, depth 8,15   { 0.0 } Hz
     800* 600, depth 8,15   { 0.0 } Hz
    1024* 768, depth 8,15   { 0.0 } Hz
    1024* 768, depth 8   { 60.0, 70.0, 74.8, 75.0 } Hz
    1152* 864, depth 8,15   { 0.0 } Hz
    1280*1024, depth 8,15   { 0.0 } Hz
    1600*1200, depth 8,15   { 0.0 } Hz

No video mode match the default one.
ALSA sound driver (device 'default')
Could not open driver 'drivers/scsi.nw': No such file or directory
MOL SCSI controller registered


    <No SCSI Devices>

    CD   /dev/cdrom       CD-ROM         <read-only>   ------ 
----> /dev/hda2 might be a boot-strap partition.
    Unembedded HFS+ /dev/hda3                       <rw> 46863 MB 
------> /dev/hda4 is linux-mounted with write privileges.
Could not open '/dev/hda4' with read-write permissions
No volumes found in '/dev/hdb'
------> /dev/sda9 is linux-mounted with write privileges.
Could not open '/dev/sda9' with read-write permissions
No volumes found in '/dev/sda'
No volumes found in '/dev/sdb'

Could not open driver 'drivers/blk.nw': No such file or directory

```

I am still a little new to linux so any help would be appreciated, thank you :)

---

### Post by gamgee911 on 2007-08-22
Nevermind, I fixed it.  I just compiled the new version that's available from sourceforge.  Thank you though.

---

### Post by ChillMonkey on 2007-08-24
what build options did you use?

---

### Post by Zaelore on 2007-08-24
I've got a quick question about mol too, what is the best way to get mac os x access to the internet within mol? Is there a guide for this anywhere? Thanks.

---

### Post by gamgee911 on 2007-08-25
Ooh, I've had so much trouble with this.  Some info would be nice if anyone had any tips.  Even better - how to control Airport modems though either Ubuntu or MOL.

---

### Post by ChillMonkey on 2007-09-05
well i got it working using the src pkg too. i'm really suprised how fast it is, even on my old mac. one bummer, i can't get same 1152x768 to work for some reason so i'm stuck with a nice black bar on the right side of my screen. oh well for now.

---

