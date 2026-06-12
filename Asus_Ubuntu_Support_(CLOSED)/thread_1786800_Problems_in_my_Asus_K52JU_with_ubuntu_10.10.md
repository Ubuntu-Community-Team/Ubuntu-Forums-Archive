---
title: "Problems in my Asus K52JU with ubuntu 10.10"
date: 2011-06-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by nshensfeek on 2011-06-20
Hi guys I recently got a an Asus K52JU laptop and had a clean installation of maverick meerkat.Got my ATI Radeon HD6370 working.But still some problems persist.Those ate enlisted below:
1.Sound comes out through the speakers even after plugging in the headphones.
2.Wireless LED doesn't turn off even after Wi-Fi is shut off
3.Inverted webcam
4.Ugly plymouth bootscreen

I got the following results after running uname-a,aplay -l, and lspci

shefeek@shefeek-K52JU:~$ uname -a
Linux shefeek-K52JU 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
shefeek@shefeek-K52JU:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
shefeek@shefeek-K52JU:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68e4
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)  







Guys please help me out so that I can show my friends why Linux is far more better than Windows.

---

### Post by lidex on 2011-06-20
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by nshensfeek on 2011-06-23
Lotta thanks budyy got ma headphones working.
Can u take care of d rest.
Thanks for d effort

---

### Post by nshensfeek on 2011-06-23
Hey greetings.
Its me again
Got ma webcam fixed.Just got it it by updatng my v4l2 libraries.:)

---

### Post by lidex on 2011-06-25
There are some fixes for the ugly plymouth screen, pick one of these:
[http://www.google.com/search?client=ubuntu&channel=fs&q=fix+for+ugly+plymouth+screen+ubuntu&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=fix+for+ugly+plymouth+screen+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by nshensfeek on 2011-06-27
Thanks for the suggestion.
But it didn't worked.

---

### Post by Coobuntu on 2012-01-08
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Hi Lidex, 

I have the same laptop that [Nshensfeek]("http://ubuntuforums.org/member.php?u=1305376") (an Asus k52JU), and I have the same problem with the headphones as well...  **The sound comes out through the speakers even after plugging in the headphones**. But the difference is that I am running Lucid Lynx (Ubuntu 10.04) 64 bit OS version on my Asus K52JU Series laptop. 

I would greatly appreciate if you can help me out too, I tried with the command that you posted but it didn't work for me and I have been for months looking for a solution but nothing works either.  

Thank you.

---

