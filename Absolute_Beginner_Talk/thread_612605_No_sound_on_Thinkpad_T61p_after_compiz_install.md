---
title: "No sound on Thinkpad T61p after compiz install"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jbrown96 on 2007-11-14
I finally got my t61p on Monday and have had lots of problems getting to sound to work. I finally followed a very simple guide to configure it. It appears as though alsa version 1.0.15rc3 works. I downloaded it using "sudo apt-get install linux-backports-modules-generic." However, i installed compiz (I use Kubuntu 7.10) and got it configured. Now the sound doesn't work. I tried running the same command again, but it says that there is nothing to update.

I think what i need to do is download alsa 1.0.15rc3 and configure the source, but I'm not sure how to do it. If someone could help me out or propose another way it would be greatly appreciated. 

Here's my hardware;

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

Thanks again

---

### Post by jbrown96 on 2007-11-14
I got it working! Here's the guide that I used. I didn't do the last step because I wasn't sure what to put instead of acer, but it worked fine after a restart. After restarting make sure to check alsamixer because it mutes some channels by default. Type alsamixer in a terminal, use left/right to select the channel, and  up/down to increase volume (m mutes/unmutes).

> sudo apt-get install libncurses5-dev build-essential gettext

get your user password when requested (you don't see nothing when you type it) then press enter.

cd $HOME
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
tar jxvf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel && make
sudo make install

cd $HOME
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
tar jxvf alsa-lib-1.0.15.tar.bz2
cd alsa-lib-1.0.15
./configure && make
sudo make install

cd $HOME
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
tar jxvf alsa-utils-1.0.15.tar.bz2
cd alsa-utils-1.0.15
./configure && make
sudo make install

And restart the system.

Guide from [https://answers.launchpad.net/ubuntu/+question/16686](https://answers.launchpad.net/ubuntu/+question/16686)

---

