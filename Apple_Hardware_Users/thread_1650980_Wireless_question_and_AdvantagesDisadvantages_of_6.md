---
title: "Wireless question and Advantages/Disadvantages of 64 bit install?"
date: 2010-12-22
forum: Apple Hardware Users
---

### Post by crazychile on 2010-12-22
I have a 6 month old MacBook Pro that I just installed 10.04 LTS on a partition, so I can do either Mac OSX or Ubuntu. I havent used it yet since I cant update any software because the internet connection isn't set up. Is it supposed to sense the wi-fi sources automatically like MAC OSX does? I have an Apple Airport Extreme, but Ubuntu is not detecting my home network.
 
So I'm wondering if my install is bad. I decided on 10.04 LTS originally thinking it may be more stable, and my school uses 10.04 LTS, but am now considering trying 10.10 because maybe it fixes my connectivity issue? My Mac is new enough to handle the 64 bit versions, but should I stick with 32bit? What are the advantages/disadvantages with the 64 bit? I am a new computer science student and just want this to work without too much tweeking to make things work. I'll be too busy trying to get code written so I don't really want to take on another project trying to make Ubuntu work for me.
 
Thanks in advance,
 
crazychile

---

### Post by TBABill on 2010-12-22
There aren't really disadvantages to either. Some people have found some niggles with various items, but I have witnessed none of those on 5 machines of different configurations. I use 64 bit exclusively unless I am running Mint Debian because it is 32 bit only, or PCLinuxOS, which is also 32 bit only.
 
Your wireless issue is just a matter of figuring out the configuration and getting the system to recognize it and activate the driver.
 
If it is internal wireless can you post the output you get after typing this into a terminal ```
lspci
``` so we can identify the chipset in use on the machine?

---

### Post by crazychile on 2010-12-22
When I type "lspci" in the terminal I get this:


central@central-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation Device 0d60 (rev a1)
00:00.1 RAM memory: nVidia Corporation Device 0d68 (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 0d6d (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0d6e (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0d6f (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 0d70 (rev a1)
00:02.0 RAM memory: nVidia Corporation Device 0d71 (rev a1)
00:02.1 RAM memory: nVidia Corporation Device 0d72 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Device 0d80 (rev a2)
00:03.1 RAM memory: nVidia Corporation Device 0d7b (rev a1)
00:03.2 SMBus: nVidia Corporation Device 0d79 (rev a1)
00:03.3 RAM memory: nVidia Corporation Device 0d69 (rev a1)
00:03.4 Co-processor: nVidia Corporation Device 0d7a (rev a1)
00:04.0 USB Controller: nVidia Corporation Device 0d9c (rev a1)
00:04.1 USB Controller: nVidia Corporation Device 0d9d (rev a2)
00:06.0 USB Controller: nVidia Corporation Device 0d9c (rev a1)
00:06.1 USB Controller: nVidia Corporation Device 0d9d (rev a2)
00:08.0 Audio device: nVidia Corporation Device 0d94 (rev a2)
00:0a.0 IDE interface: nVidia Corporation Device 0d85 (rev a2)
00:0b.0 RAM memory: nVidia Corporation Device 0d75 (rev a1)
00:0e.0 PCI bridge: nVidia Corporation Device 0d9a (rev a1)
00:15.0 PCI bridge: nVidia Corporation Device 0d9b (rev a1)
00:16.0 PCI bridge: nVidia Corporation Device 0d9b (rev a1)
00:17.0 PCI bridge: nVidia Corporation Device 0d76 (rev a1)
01:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation Device 08a0 (rev a2)
central@central-laptop:~$ 


Thank you for your help.
crazychile

---

### Post by TBABill on 2010-12-22
> 02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) That's your wireless device. Broadcom requires the use of a proprietary driver. Go to System>Administration>Hardware and install the STA driver. You need to be connected via wired ethernet to do so. Here's a link to help with other aspects of a Macbook if needed (for Maverick). [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

---

### Post by crazychile on 2010-12-22
Thanks TBABill, I'll give that a try when I have some time over the holidays.

crazychile

---

