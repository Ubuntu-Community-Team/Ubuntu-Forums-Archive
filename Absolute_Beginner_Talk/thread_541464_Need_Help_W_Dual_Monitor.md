---
title: "Need Help W/ Dual Monitor"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-09-02
Following [This]("http://ubuntuforums.org/showthread.php?p=1773544") HowTo...

Im on step 4.

This is my terminal where I was running the commands.
> 
payton@the-Desktop:~$ sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 17.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112456 files and directories currently installed.)
Removing xorg-driver-fglrx ...
payton@the-Desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
01:0c.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 10)
payton@the-Desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US                      
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
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
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
payton@the-Desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6143kB of archives.
After unpacking 17.6MB of additional disk space will be used.
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 112430 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.29_i386.deb) ...
Setting up xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.5-16.29) ...
payton@the-Desktop:~$ gksudo gedit /etc/default/linux-restricted-modules-common

(gedit:5963): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
payton@the-Desktop:~$ sudo depmod -a
payton@the-Desktop:~$ sudo aticonfig --initial --overlay-type=Xv
Uninitialised file found, configuring.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
payton@the-Desktop:~$ sudo aticonfig --desktop-setup=horizontal --sync-vsync=on --add-pairmode=Width0xHeight0+Width1xHeight1
[color="red"]FGLRX_AddPairMode failed when try to add mode[/color] : 0x0+0x0 
Warning: Option 'DesktopSetup' doesn't affect running session.
Warning: Option 'Capabilities' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
payton@the-Desktop:~$ sudo aticonfig --query-monitor
  Connected monitors: none
  Enabled monitors: none
payton@the-Desktop:~$ man fglrx
No manual entry for fglrx
payton@the-Desktop:~$ 

TIA.

---

### Post by pgar23 on 2007-09-02
BTW I have 2 graphics cards...

1st:
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

2nd:
ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

---

### Post by Hobo Joe on 2007-09-02
sounds like it's considering your integrated as the primary card. Are you sure the other one is hooked in properly? Becuase it should autmatically override the integrated card.


But in the end, I'm not sure it really matters, becuase an 82845 is about the same as a 7500, and ATi drivers are pain.

---

### Post by pgar23 on 2007-09-02
> **Hobo Joe said:**
> sounds like it's considering your integrated as the primary card. Are you sure the other one is hooked in properly? Becuase it should autmatically override the integrated card.


But in the end, I'm not sure it really matters, becuase an 82845 is about the same as a 7500, and ATi drivers are pain.

I have the BIOS set up so that the integrated card is the primary, and yes I am positive the ATI is hooked in properly because I tested the Dual Monitor on XP and it was working properly.

I want to Dual Monitor, I dont want my ATI overriding my Intel.

---

### Post by Hospadar on 2007-09-02
You might try making your ATi the primary,  Also just to be sure, your ati card has a single output so you want to use that output and the intel output for your dual monitor setup?

If your ATi card has two outs that would I'm sure be easier.

---

### Post by pgar23 on 2007-09-02
> **Hospadar said:**
> You might try making your ATi the primary,  Also just to be sure, your ati card has a single output so you want to use that output and the intel output for your dual monitor setup?

If your ATi card has two outs that would I'm sure be easier.

When I make the ATI card my primary, i get an xorg problem  and ubuntu wont boot to the GDM, so I use the Intel card as my primary and ubuntu boots correctly. Therefore I would prefer my Intel card be the primary. 
My ATI card has two outs but I dont have the cords for the other one, its not the regular cord that goes from monitor to graphics card.

And Hobo Joe was indeed correct, ATI drivers ARE A PAIN! lol
ATI and Ubuntu are not easily compatible.

Is there any way to DUAL MONITOR w/ my Intel card being the primary and ATI card as secondary?

---

### Post by pgar23 on 2007-09-03
Following new tutorial...[EASIER]("http://ubuntuforums.org/showthread.php?t=278797")

Im getting the other screen when running
```

X -configure
```

After running that, I get:
1. blah
2. blah
3. blah
...
11. X(FontFileCompleteXLFD+0x1e1) [0x80T3ab1]

Fatal Server Error:
Caught Signal 11. Server aborting

Aborted

...And on the other screen it reads: RV200 113-G0116-100 BIOS

What the Heck? 
what does this mean? 
Anybody know what to do?

---

### Post by pgar23 on 2007-09-03
*bump*

---

### Post by pgar23 on 2007-09-04
*bump*

---

### Post by pgar23 on 2007-09-04
*bumpidy bump bump* for help

---

### Post by mrphantastic on 2007-09-04
Ok pgar23, I think I can help, cuz as we speak, I'm on a dual-monitor, dual-booted system :)  First of all though, I'm kinda confused by all the above posts...catch me up...you've got a chipset Intel Gfx Processor "Built-On" to your MotherBoard...and the separate device with 2 outputs, that causes you compatibility issues with Ubuntu 7.04 is the ATI Graphics Card?  AND, you seem to "lack" the devices/adapters necessary to connect the screens you have to the double-output ATI device?

---

### Post by pgar23 on 2007-09-05
found the driver for my card [Here]("http://driverscollection.com/?H=All-in-Wonder%20Radeon%207500&By=ATI")

---

