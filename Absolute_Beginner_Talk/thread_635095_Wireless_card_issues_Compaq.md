---
title: "Wireless card issues Compaq"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by blane2 on 2007-12-08
So I've managed to get Ubuntu gusty installed and duel booted with no problems what-so-ever. I find this to be some what of an accomplishment in-and-of itself as I've been using Linux for all of about 4 hours now. 

I'm currently only having one major problem, my laptop's wireless network card. I've searched the internet and these forums far and wide in search of a simple and easy to understand solution to my problem but I can't seem to find one and I'm dying of information overkill. 

I gathered that i need to install ndiswrapper-util-1.9 , ndiswrapper-common , and ndisgtk . According to the synaptic Package Manager all three of these things are installed. Though i'm not sure if they are

I've also read that i need to download a specific driver for my card. At one point i had a terminal command that would show the information for my system, but honestly i've been trying a million different ways for the last 4 hours 
and i'm running around in circles feeling like i'm missing some super important step.

PLEASE help me to get this wifi card working in the compaq presario c700T series notebook.


forever in debt to your priceless advice.

---

### Post by blane2 on 2007-12-08
> lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


These are my results from lspci

i've also tried the steps outlined on the first page of this thread
[Gutsy on HP and Compaq Laptops]("http://ubuntuforums.org/showthread.php?t=529336")

I feel like it's a bit over my head, and i know it is because i can't seem to get it to work for me. though many others reported it working for them.

---

### Post by schwascore on 2007-12-08
I have the same chipset, this method worked for me:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by jetpeach on 2007-12-27
were you able to get the wireless working ok? i'm thinking about buying a c700t right now but wonder how much trouble it is to get working well with ubuntu..

---

