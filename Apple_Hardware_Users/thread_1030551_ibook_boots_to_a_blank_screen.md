---
title: "ibook boots to a blank screen"
date: 2009-01-04
forum: Apple Hardware Users
---

### Post by darkkenchild on 2009-01-04
Well, not quite. It loads to a black screen with a bar across it that color shifts...

Anywho.

I'm very, very new to Ubuntu (and Linux in general), having been a Windows user for about 15 years now, so please be gentle.

I've been fighting with an old iBook I inherited from a friend to get Ubuntu on it. I'm not certain, but I believe it is specifically this release of the beast:
[http://www.everymac.com/systems/apple/ibook/stats/ibook_700_14.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_700_14.html)

To my problem:

I fought for a few weeks to install the OS onto the beast, and by all indications, I finally got Dapper Drake (6.06.2) to fully install with no crashes/etc. (I got Gibbon to work as well, but ran into a similar problem, I figured that it was too much for the old laptop, so I downgraded as low as I could find).

However, it now seems to boot fine. I hear a chime, and I can log in (as near as I can tell with a mostly empty screen), which produces more chimes. Having perused the internet (both on the Ubuntu site and beyond), I have come across a known issue with the xorg.conf, to which it is recommended that I access a prompt through "ctrl+option(alt)+F1(-F6)." All this acheives is a blank screen (which pulses slightly), and no prompt. 

Any ideas?

---

### Post by mkvnmtr on 2009-01-04
My G4 Ibook runs fine with 8.04. There were a couple of things starting to install that I had to do but they were simple. Tell us what Ibook you are on and what the specs are. I bet you can run Ubuntu with few problems.

---

### Post by darkkenchild on 2009-01-04
There's a link to the specs above, but for simplicity's sake, I'll post it here:

# CPU: 600/700 MHz G3 (PowerPC 750fx)
# bus: 100 MHz
# performance:

    * Geekbench 2 (Tiger): 318 (600 MHz), 353 (700 MHz)

# ROM: 4 MB, NewWorld ROM in RAM architecture
# RAM: 128 MB of SDRAM soldered in place, expandable to 640 MB using one 1.25" 3.3V PC100 compliant SO-DIMM
# Level 2 cache: 512 KB on-chip cache
# Video: ATI Mobility Radeon with 2x AGP
# VRAM: 16 MB
# display: 12.1" 24-bit SVGA (1024 x 768) color active matrix, resolution scaling for 640 x 480 and 800 x 600 modes
# video out: VGA and composite video
# hard drive: 20/30 GB UltraATA-66
# media drive: 8x8x8x24x Combo (CD-RW/DVD), 24x CD-ROM on 600 MHz model
# floppy drive: external USB only
# expansions bays: none
# USB: 2 USB 1.1 ports
# FireWire: 1 FW400 port
# ethernet: 10/100Base-T
# modem: v.90 56k
# WiFi: 802.11b AirPort optional
# microphone: built in
# PC Card slots: none
# Battery: rated at 5 hours
# size: 11.2 x 9.1 x 1.35" (28.5 x 23.0 x 3.4 cm)
# weight: 4.9 pounds (2.2 kg) with battery

---

### Post by mkvnmtr on 2009-01-04
OK 128 Mb of ram is probably not enough to run Ubuntu well enough to use it. If youo don't want to double your ram or even go to 512 Mb you probably won't be happy with the results. The good news is you can get a distro on your machine that will work but it will be some work. There is a minimal Ubuntu install for ppc. It wont be Ubuntu with the gnome desktop but it can be a very useable. You will need to Google Ubuntu minimal install and study a couple of the tutorials. It will also help you if you scan a couple of then threads here on installing on G3 Ibooks. Some of the other minimal installs may mot be for ppc. When you decide what to install there are some guys here with a good bit of experience on ppc machines.

---

