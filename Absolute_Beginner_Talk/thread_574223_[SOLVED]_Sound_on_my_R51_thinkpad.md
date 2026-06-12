---
title: "[SOLVED] Sound on my R51 thinkpad"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by wahoobob on 2007-10-12
I had the hard drive go out and so I reinstalled 7.04.  Now the darn sound won't work and everything seems to think its working,  but no sound...  I un-muted everywhere.  I hope there is a fix I am overlooking.  All help will be appreciated.  Be gentle, I am a real NOOB.  I had this problem once before on the first install and now my fix from that time is not working.
:confused:

WahooBob

---

### Post by ronmarley1 on 2007-10-12
> **wahoobob said:**
> I had the hard drive go out and so I reinstalled 7.04.  Now the darn sound won't work and everything seems to think its working,  but no sound...  I un-muted everywhere.  I hope there is a fix I am overlooking.  All help will be appreciated.  Be gentle, I am a real NOOB.  I had this problem once before on the first install and now my fix from that time is not working.
:confused:

WahooBob

I'm not sure how I can help, but I'm willing to try.  I have an R51, but I've never had a problem with sound.  I'd be will to compare my settings to yours, if you want.  Unfortunately, I'm leaving in about 10 minutes and won't be home for about 4-5 hrs.  Let me know...

---

### Post by wahoobob on 2007-10-13
I just got your message.  So, I don't know how to send you the settings you want.  Can you give a method that will be fairly easy?  The crazy thing is the sound works with the system running from the disk, and it worked fine on 7.10 upgrade that was running prior to the crash.  Its probably something really stupidly simple, a driver or something, but I can't find it and if I keep mucking around in the system enough, knowing my limitations, I'll stop some other function.  Anyone out there can help?
 
Wahoobob

Some preliminary info:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

then I did this in terminal:  
~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0557
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: IBM Unknown device 0557
        Flags: fast devsel
        Memory at e8000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at d0080000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at d0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=64
        I/O behind bridge: 00003000-00007fff
        Memory behind bridge: d0200000-dfffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Memory at 60000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM Unknown device 0554
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at d0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at d0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=04, sec-latency=176
        Memory window 0: f0000000-f3fff000 (prefetchable)
        Memory window 1: d4000000-d7fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation Unknown device 2551
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
        Subsystem: IBM Thinkpad R50e model 1634
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0201000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 7000 [size=64]
        Capabilities: <access denied>

Does this show you anything?

---

### Post by ronmarley1 on 2007-10-13
I went ahead a did some screen captures of the Sound Preferences window and also of alsamixer running in a terminal window.  Maybe these will help?  Maybe reinstall alsa?

---

### Post by wahoobob on 2007-10-13
OK, I made mine look just like that, and still no sound.  I also looked for udates like this:
bob@bob-laptop:~$ sudo apt-get update && sudo aptitude dist-upgrade
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Do you know the name of the driver and I can sudo modprobe to get it?

---

### Post by wahoobob on 2007-10-13
> **ronmarley1 said:**
> I went ahead a did some screen captures of the Sound Preferences window and also of alsamixer running in a terminal window.  Maybe these will help?  Maybe reinstall alsa?

How do I reinstall ALSA?

---

### Post by ronmarley1 on 2007-10-14
Open Synaptic (System, Administration, Synaptic Package Manager) and search for alsa and reinstall alsa-base.  It seems really strange that it works with the live CD but not the install...

---

### Post by wahoobob on 2007-10-14
Computers... Can't live with them and can't live without them,  but after changing all the settings one more time and still no sound I rebooted again and Voila! the speakers were so loud they scared me to death.  I guess there was some conflict in the bootup because now it works...  Thanks for your suggestions and the settings screen shot.

---

### Post by ronmarley1 on 2007-10-15
Yea for you!  Glad I could help.

---

