---
title: "install drivers"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-01-10
I Just Installed Ubuntu 7.10 On My Dell Vostro 1500 Lap.the Audio And Video And Other Devices Are Not Working..how To Install The Drivers And Where To Download Them???plz Tell A Website To Download Them
VOSTRO -1500 MODEL
2GB, DDR2, 667MHz 2 DIMM 
120G 5400RPM SATA Hard Drive 
Vostro 1500, Intel Core 2 Duo T5470, 1.6GHz, 800Mhz FSB, 2M L2 Cache 
128MB NVIDIA GeForce 8400M GS

---

### Post by taurus on 2008-01-10
Can you list the spec of your machine?  Changes are Gutsy comes with the drivers for your laptop.

---

### Post by balaknair on 2008-01-10
Hi Rajesh
Ubuntu 7.10 (Gutsy) comes with most drivers already on the CD. Only certain drivers need be installed seperately.
Copy paste "lspci -v" (without quotes) in a terminal(Applications menu>Accesories>Terminal, or System>Konsole if you're using Kubuntu) and post the output.
This will give others a clue about what set-up you have and what devices Ubuntu is detecting. Once the problems are sorted out and identified, it becomes easier to fix them.

For the nVidia GeForce 8400, you can install the restricted nVidia drivers using the restricted drivers manager(System menu>Adiministration>Restricted Drivers Manager). Just click to enable it, and Ubuntu will download and install it for you. This is much simpler than downloading from some site and installing(and safer). 
For sound, WiFi and other stuff, copy paste the output you get with lspci -v, and we'll find out what the problems are and how to solve them one by one.
Wishing you luck

---

### Post by taurus on 2008-01-10
I am not sure why you even created another thread of the same topic?

[http://ubuntuforums.org/showthread.php?t=663761](http://ubuntuforums.org/showthread.php?t=663761)

---

### Post by stchman on 2008-01-10
> **RAJESHKSV said:**
> I Just Installed Ubuntu 7.10 On My Dell Vostro 1500 Lap.the Audio And Video And Other Devices Are Not Working..how To Install The Drivers And Where To Download Them???plz Tell A Website To Download Them
VOSTRO -1500 MODEL
2GB, DDR2, 667MHz 2 DIMM 
120G 5400RPM SATA Hard Drive 
Vostro 1500, Intel Core 2 Duo T5470, 1.6GHz, 800Mhz FSB, 2M L2 Cache 
128MB NVIDIA GeForce 8400M GS

Yes, post an lspci -v output here.  We need to know what kind of sound card you have.

You can try Envy for the Nvidia 8xxx card.

---

### Post by RAJESHKSV on 2008-01-24
as per your directions i entered the command lspci -v in the terminal and this is the output....my sound card is sigmatel high definition audio...


rajeshksv@rajeshksv-supercomputer:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0228
        Flags: fast devsel, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f9f00000-f9ffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f9c00000-f9efffff
        Prefetchable memory behind bridge: 00000000f8000000-00000000f81fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f9b00000-f9bfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=32]
        Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 0228
        Flags: medium devsel, IRQ 10
        Memory at febfb700 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f4000000 (64-bit, prefetchable) [size=64M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        Expansion ROM at fea00000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 0228
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

rajeshksv@rajeshksv-supercomputer:~$

---

### Post by balaknair on 2008-01-24
For the ICH8 sound cards, you need the ALSA 1.0.15 modules.
The easiest way to install them on Ubuntu 7.10 is described below
Step 1:
Enable backports repositories
System menu> Administration> Software sources---> Updates---> enable Backports (Unsupported updates)
Step 2:
Open a terminal and enter this command to download and install the backports modules
sudo apt-get install linux-backports-modules-generic

Step 3:
Reboot, then in Alsamixer unmute all channels.

---

### Post by RAJESHKSV on 2008-01-25
thank you very much for your assistance..finally i am able to hear sound in ubuntu..thanks a lot...and plz tell me how to install video drivers??i have installed beryl but its not working..when i click on beryl manager it is showing white screen and then its not responding...i have to reboot the system for normal functioning..plz help me...

---

### Post by balaknair on 2008-01-26
The easiest way to install the proprietary drivers is to just enable restricted drivers
System menu> Administration> Restricted Drivers Manager. It'll download the drivers and install them. Then enable direct rendering and in System> Preferences> Appearance -->Visual effects you can enable the compiz eyecandy. You can also check out a number of threads on Ubuntuforums dedicated to Compiz and Beryl.

I Use a 8400GS 512MB card, and this is what worked for me in Gutsy(I had a whole truckload of problems with Beryl and Nvidia on Feisty). Compiz-fusion runs great now.
The other easy way is to download and install Envy- it's a script by Alberto Milone which willl download and install the drivers for you. You can further instructions here
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Whichever method you use, backup your Xorg.conf file file first.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

To restore the backup from command line or recovery mode 
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

Just to be on the safe side I advise you to print out the page FAQ or at least write down the important commands so that you can restore the failsafe drivers from the command line should you lose the GUI- I say this because of my experiences with Feisty+nVidia.
Restoring the failsafe is easy enough, but you do have to know the commands.

All the best.

---

### Post by RAJESHKSV on 2008-01-26
many many tqs for ur guidance.i have a small problem..i have downloaded .deb file from net..but how to install it thr terminal??if we pess sudo apt-get install <filename>
its again downloading from net..it is not using the file i have downloaded..wt 2 do??

---

### Post by taurus on 2008-01-26
```
sudo dpkg -i **filename.deb**
```

---

### Post by balaknair on 2008-01-26
Double click on the .deb file, it'll ask for your password and install

---

### Post by RAJESHKSV on 2008-01-27
plz tell me how 2 install a exe file using wine...can we run multiple exe files at a time using wine..which type of exe files will not be installed using wine??:confused:

---

