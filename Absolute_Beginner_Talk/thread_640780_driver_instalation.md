---
title: "driver instalation"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by 2manydrugsago on 2007-12-14
i have an old 3dfx vodoo 3 card , i found the driver but have no idea how to install it. please help. thx in advance

---

### Post by flamelab on 2007-12-14
Where did you find it ?On Synaptic ?
Post the URL (if it was on a site ) or else just download the driver from the Synaptic fearlessly .

---

### Post by logos34 on 2007-12-14
Have you tried the voodoo driver already installed?

sudo dpkg-reconfigure xserver-xorg

>autodetect hardware OR say 'no' and select 'voodoo' at the bottom


If not, give some more info on the driver you downloaded

---

### Post by 2manydrugsago on 2007-12-14
[http://packages.debian.org/source/sid/xserver-xorg-video-tdfx](http://packages.debian.org/source/sid/xserver-xorg-video-tdfx) from a google search

---

### Post by 2manydrugsago on 2007-12-14
updating with add remove right now my terminal is slower than the withdraw from iraq

---

### Post by logos34 on 2007-12-14
> **2manydrugsago said:**
> ...my terminal is slower than the withdraw from iraq

LOL!

---

### Post by logos34 on 2007-12-14
yeah, flamelab is right--it's right there in the repos

(i'm on x64 gutsy, but it should be the same for x86):
> $ apt-cache show xserver-xorg-video-tdfx
Package: xserver-xorg-video-tdfx
Priority: optional
Section: x11
Installed-Size: 148
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Version: 1:1.3.0-1ubuntu1
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-tdfx
Provides: xserver-xorg-video-1.0
Depends: libc6 (>= 2.5-0ubuntu1), xserver-xorg-core (>= 2:1.1.1-11)
Conflicts: xserver-xorg-driver-tdfx
Filename: pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.3.0-1ubuntu1_amd64.deb
Size: 39672
MD5sum: 080bc0ae831a1f48f346a0840ad2c03a
SHA1: 02d3719ec17486f157fa32d60478fe9b7b4de7ed
SHA256: 2973265897cdc7e3eced69f79838603a4939dfb2854797a50ca611c0a5829073
Description: X.Org X server -- tdfx display driver
 This package provides the driver for 3dfx Voodoo video cards and their
 derivatives.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'driver/xf86-video-tdfx' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, edubuntu-desktop-kde, xubuntu-desktop, gobuntu-desktop

It's already installed on mine.  Try the dpkg-reconfigure routine I posted above.

---

### Post by 2manydrugsago on 2007-12-14
how do I identify my bideo cards bus identifier?

---

### Post by 2manydrugsago on 2007-12-14
i have no idea what you mean so picture a bunny with a pancake on its head

---

### Post by logos34 on 2007-12-14
you can accept the defaults for the most part...the only thing you might have to change is the monitor settings and keyboard or mouse

---

### Post by 2manydrugsago on 2007-12-14
I did the sudo dpkg-reconfigure xserver-xorg  and  finaly go thru all the sections . now how do I change my resultion and refreshrate, the system, prefernces, screen resulotion is stuck on  640x480. what did I do wrong?

---

### Post by logos34 on 2007-12-14
if you told it to save settings to xorg file, then reboot and hopefully you'll have more options in sys>prefs>scr res

---

### Post by 2manydrugsago on 2007-12-14
now i cant to get the GUI to load. it  tries to find the  vodoo driver and says its not there. then i get a prompt,  not what i had hoped.no gui   and i dont know  anny commands to start it even if it would have the driver. im stuck using the live cd on a 700mhx and 128 of pc100 ram Do I have to reinstall again?

---

### Post by logos34 on 2007-12-14
mount root partition and go 

cd /media/disk/etc/X11

ls xorg*

dpkg-reconfigure should have created a xorg.conf.bak or .backup or xorg.conf~ copy of original.  Copy it back with:

sudo cp xorg.conf.bak xorg.conf

Either that or reboot and go into recovery mode and run sudo dpkg-reconfigure... again at the command prompt.  But this time choose the original driver it was using or try the 'vesa' driver

---

### Post by 2manydrugsago on 2007-12-14
back to the live cd again.  the messge said  that it didnt know what package  to reconfigure . it tales me  10 min to boot the live cd  so  If ther is another way to get my gui back ill start over

---

### Post by logos34 on 2007-12-14
> **2manydrugsago said:**
> back to the live cd again.  the messge said  that it didnt know what package  to reconfigure .

I meant run sudo dpkg-reconfigure **xserver-xorg** again.  

Hopefully that will get you back to the gui.  Or copy back the old (backup) xorg.conf like I said earlier. You can do just it the same  in the recovery console.  I know working in the console vs. the gui desktop on the live cd is kind of intimidating, but you can do most everyhting from it.

---

### Post by 2manydrugsago on 2007-12-15
What if it asked for the  bus ID agaiin?

---

### Post by 2manydrugsago on 2007-12-15
If I run the sudo dpkg reconfigure xserver-xorg thing it will ask me what my vid cards bus ID. and i have no idea how to find this out. You say it is in Synamptic  but I need a gui to start it and then I dont know how to find a vid card driver in it  I am  Super Ubuntu Noob (i have a cape and everything)

---

### Post by 2manydrugsago on 2007-12-15
and a badger ( he has a cap too)

---

### Post by logos34 on 2007-12-15
try 

$ lspci

you'll get something like this:
> ~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
[COLOR="Red"]**00:05.0 **[/COLOR]**VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)**
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

mine's '00:05.0' on the PCI bus

---

### Post by 2manydrugsago on 2007-12-15
I will try. and my badger will be happy too.

---

### Post by 2manydrugsago on 2007-12-15
If I boot into normal mode for my ubuntu 6.06 it comes up with a command prompt. I log in and  type sudo dpkg-reconfigure xserver-xorg  and  select vesa card driver instead of vodoo?  then if it askes  try  00:05:0  for bus ID  then continue with  mouse/kb/monitor setup . I know it is not 01:00:0 for the bus ID. Is this all i need to do?

---

### Post by logos34 on 2007-12-15
yep, try vesa first...use whatever lspci shows as the graphics device for your pc...as I recall the only thing I have to worry about when I run dpkg-reconfigure xserver-xorg is that the vert and horiz refresh rate are detected correctly or add them manually (I haven't had to do that in a long time--they're auto detcted).  I believe that's all.  Then finish and hit ctrl+alt+F7 to start the X server, or type 

sudo /etc/init.d/gdm start 

or reboot.

I wish I knew why it's having such a hard time.

---

### Post by 2manydrugsago on 2007-12-15
no luck. am I going to have to reinstall?

---

### Post by logos34 on 2007-12-15
hard to tell what's happening...from the recovery console command prompt, try 

ls /etc/X11/xorg.conf*

then take a look at each xorg file to see if there is one that has the original video driver still listed (i.e. that hasn't been edited by your attempts at dpkg-reconfigure).

cat /etc/X11/xorg.conf... (try each one listed in above output).

If you find it, copy it back with the cp command I gave earlier.

But that will only get you back to square one with original low res

You could reinstall but use **X**ubuntu this time (which is what you should be running on those hardware specs anyway)

---

### Post by 2manydrugsago on 2007-12-15
no cd burner on this  box,  how do i tell what the original low res file was?

---

### Post by logos34 on 2007-12-15
'driver' line in 'device' section.  Mine:

> Section "Device"
    Identifier        "Generic Video Card"
**    Driver              "nvidia"**
    VendorName    "NVIDIA Corporation"
    BusID               "PCI:0:5:0"
    BoardName      "GeForce 6100"
    Option              "NoLogo" "True"
   
EndSection

---

### Post by 2manydrugsago on 2007-12-15
can I  run terminal and  check without leaving the live cd?

---

### Post by 2manydrugsago on 2007-12-16
I reinstalled and joy of joys  i get a grub error 17  how do i get kubuntu shipped to me?
Kubuntu will find my hardware right?

---

### Post by logos34 on 2007-12-16
> **2manydrugsago said:**
> I reinstalled and joy of joys  i get a grub error 17  how do i get kubuntu shipped to me?
Kubuntu will find my hardware right?

talk about bad luck...

I think you'll have the same problems on kubuntu.  could be wrong though.  Isn't there a ShipIt version of kubuntu?

error 17:
[http://www.users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux](http://www.users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux)

---

### Post by 2manydrugsago on 2007-12-16
i have  7.04 and 7.10  disks  maybe i shouls reinstall with one of them. i know why the grub error happen the power blinked and i had to restart during the partitioning

---

