---
title: "Ubuntu 7.10 installation crashes."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by T-Rexx on 2007-10-29
I can't get ubuntu 7.10 to boot "live" on a Gigabyte GA-81865GVMK motherboard with a 3.0 GHz Intel Pentium 4, 2 GB RAM, and Intel "Extreme Graphics 2" video integrated onto the board. I have an impression that the integrated Intel video subsystem is tripping up the installer. I say this because the installation crashes immediately after the initial boot screen displays.

The initial screen offers a selection of "installation" parameters for the "live" session, and displays normally. No matter what parameters I select, however, the installation crashes immediately after the initial screen. The crashes always result in a corrupted display screen of unreadable nonsense. 

Oddly, ubuntu 7.04 has absolutely no problem with this same video chipset, and configures it automatically. I am, in fact, posting this from ubuntu 7.04 running "live" on the same computer, with a 1280 x 1024 display. 

Here is the output of lspci:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:00.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:00.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:01.0 Serial controller: Integrated Technology Express, Inc. IT8874F PCI Dual Serial Port Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
ubuntu@ubuntu:~$ 



What do I need to do to get ubuntu 7.10 to boot on (and install to) this computer? 

[I cannot install ubuntu 7.04 (which does seem to run just fine on this system) and them upgrade to 7.10, because ubuntu 7.04 cannot see the SATA drives on this system (and that's where I want to install it. I'm guessing ubuntu 7.10 would be able to see the SATA drives, if I could only get it to boot "live".).]

Thanks.

---

### Post by Martje_001 on 2007-10-29
Try installing ubuntu from a alternate-cd.

---

### Post by Jimmyfj on 2007-10-29
If Ubuntu 7.04 runs well on your system you might want to do an online upgrade from 7.04 to 7.10. 

An online upgrade takes time and open up to upgrade errors, but it's worth a try just to upgrade an existing 7.04 install with the command:** sudo update-manager -d** in a terminal.

Otherwise you could try downloading the alternate install Cd, or, before doing so, try booting the live Cd in safe graphics mode.

---

