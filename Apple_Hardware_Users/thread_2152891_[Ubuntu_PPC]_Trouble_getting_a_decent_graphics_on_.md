---
title: "[Ubuntu PPC] Trouble getting a decent graphics on Powerbook G4 DVD liveboot"
date: 2013-06-09
forum: Apple Hardware Users
---

### Post by manu27993 on 2013-06-09
Hi..
My 15" Powerbook G4 (AL) was getting too old and Mac OSX Lion installed by default on it was too boring to use as my daily driver..

So.. I decided to install Ubuntu 13.04 PowerPC version on it..

I downloaded the LiveDVD Image, burned it to a Disc and quickly tried to boot it on my Powerbook..

I got the Yaboot Prompt..

I directly pressed enter.. Ubuntu Boot screen appeared with "Ubuntu 13.04" text and four running dots.. and then after two to three flickers, I got a mouse pointer.. then highly unusable low graphics... with crazy grid-like grey dots and all... I pressed Ctrl+Alt+fn+F1... got a terminal screen... typed "lspci" and got the following output:

```

0000:00:0b.0 Host bridge: Apple Inc. Intrepid2 AGP Bridge
0000:00:10.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350/M10 [Mobility Radeon 9600 PRO Turbo]
0001:10:0b.0 Host bridge: Apple Inc. Intrepid2 PCI Bridge
0001:10:11.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:10:14.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:15.0 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:10:15.1 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:10:15.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O
0002:24:0b.0 Host bridge: Apple Inc. Intrepid2 PCI Bridge
0002:24:0d.0 Unassigned class [ff00]: Apple Inc. Intrepid2 ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Inc. Intrepid2 Firewire
0002:24:0f.0 Ethernet controller: Apple Inc. Intrepid2 GMAC (Sun GEM)

```

I didnt know what to do.. so tried with "live-nosplash" yaboot parameter..
I got sequences of text... then got a display with too less colors... but looks as if a light ray is emerging out from the bottom left corner... but again unusuable... then again could get a terminal as before...

then for my 3rd attempt.. tried "live video=ofonly" parameter...
I got a blue colored boot screen with running dots.. but proper ubuntu logo this time... booted up to a black screen... when i increased the brightness, I got "The system is running in low-graphics mode" dialog box... colors were proper this time... after clicking on OK.. I got options to configure graphics manually... As I havent done this before, I dont know what to do... but again was able to get a terminal screen as before...

then for my 4th attempt.. tried "live nomodest" parameter...
got boot screen and graphics after boot as i got in my 1st attempt... terminal worked too..

I'm out of options... Please help me out here...

---

### Post by abtabt on 2013-06-09
can this help

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

---

### Post by manu27993 on 2013-06-09
> **abtabt said:**
> can this help

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

I get this and hangs:

[    85.981243] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    85.981731] b43-phu0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    85.982136] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructons on this website.

---

### Post by michiganmac on 2013-06-09
> **manu27993 said:**
> I get this and hangs:

[    85.981243] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    85.981731] b43-phu0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    85.982136] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructons on this website.


Type the following at the boot: prompt

```
live b43.blacklist=yes
```

This is covered in the wiki at:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by manu27993 on 2013-06-09
pls tell me in short what to do... I still find these stuff too alien to me... I tried doing this with no result:
```
live b43.blacklist=yes video=offb:off radeon.modeset=0 single
```

It boots up to show this message and hang...
[    82.677086]  b43: 'yes' invalid for parameter 'blacklist'

I tried blind-typing "modprobe aty128fb mode_option=1024x768-16" and pressed enter... nothing happened... 
I tried blind-typing "Xorg -configure" and pressed enter, blind-typed "start lightdm"... nothing happened...

This is really frustrating... :icon_frown:

---

### Post by michiganmac on 2013-06-09
> **manu27993 said:**
> pls tell me in short what to do... I still find these stuff too alien to me... I tried doing this with no result:
```
live b43.blacklist=yes video=offb:off radeon.modeset=0 single
```

It boots up to show this message and hang...
[    82.677086]  b43: 'yes' invalid for parameter 'blacklist'

I tried blind-typing "modprobe aty128fb mode_option=1024x768-16" and pressed enter... nothing happened... 
I tried blind-typing "Xorg -configure" and pressed enter, blind-typed "start lightdm"... nothing happened...

This is really frustrating... :icon_frown:

These suggestions are for booting the Live CD of Lubuntu (PPC), not Ubuntu (PPC). I haven't heard of anyone being able to boot the Live CD of regular Ubuntu on a PPC since version 12.04 LTS.

For Lubuntu, here's what I would try first for a radeon card:

```
live b43.blacklist=yes video=radeonfb:1024x768-32@60
```

Substitute whatever resolution your Powerbook display uses for the "1024x768-32@60" part.

---

### Post by manu27993 on 2013-06-09
wonderful... that seemed to work... thanks a lot... <3....

Oh... wait a minute... where is the desktop... I can only see the pointer, notifications and a black screen... no unity panel, top panel or desktop icons and background...

---

### Post by michiganmac on 2013-06-09
> **manu27993 said:**
> wonderful... that seemed to work... thanks a lot... <3....

Oh... wait a minute... where is the desktop... I can only see the pointer, notifications and a black screen... no unity panel, top panel or desktop icons and background...


As I said in my former reply, this workaround is for Lubuntu. I haven't talked to anyone able to boot the Live CD of Ubuntu, newer than 12.04 LTS, on a PPC.

Sorry.

---

### Post by manu27993 on 2013-06-10
This seems right to me.. 
```
live-nosplash b43.blacklist=yes radeon.modeset=0 video=offb:off video=radeonfb:1440x960-32@60
```

b43 is blacklisted
kms is disabled
openfirmware framebuffer is disabled
forced a framebuffer mode

But raedonfb is loaded as a kernel module in live mode.. so the line "radeonfb mode_option=1440x960-32@60" must be added to /etc/modules 

and line "radeonfb" should be added to /etc/initramfs-tools/modules

followed by "sudo update-initramfs -u" on terminal screen...

but this is not persistent as I'm booting from a LiveDVD.. Any workaround for this?

---

