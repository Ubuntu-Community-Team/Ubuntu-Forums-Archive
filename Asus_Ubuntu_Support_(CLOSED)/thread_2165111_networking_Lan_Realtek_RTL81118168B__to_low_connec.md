---
title: "networking Lan Realtek RTL8111/8168B  to low connection &amp; more trouble"
date: 2013-08-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Eglefino on 2013-08-03
I find every where solutions for Networking & Wireless but not for wired. I've a Asus P6T standard with the Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02) but my connection every-time is 100 Mb/s at eth0, must be 1000Mb/s

All problems came after my ISP gave me a new cable-router/modem with telephone (docsis3.0) it is set in dhcp 192.168.178.13.

Before I had a own Netgear wdr3700 all set with addresses of my Windows-period (10.0.0.1). the cable-installer could not change the addresses to the new modem, because it did not changing at all. So I did it myself on * good luck * with text found on the internet.

I have more problems w ith the flash-plugin (?) I  think that's the problem, I cannot type freely because the keyboard forgot/forget with every word some keys My Logitech mouse even not function well (Anywhere M).... I'm bedridden and disabled d working with 12.04 at this way is really terrible! I have less energy but with the speed problems I get no normal video to see about p.e. the Guardian.uk I cannot type a Twitter-message or something in Gedit/Leafpad. I have no energy to take out of my message the mouse-problems to the mouse-problems in the forum and the keyboard-problems to the keyboard-forum.
My Logitech keyboard a Lightning K-800 wireless

All my hardware was pretty working with Lucid Lynx but with Precise Pangolin nothing is working well, even my mfp Samsung CLX-3185FW is not installed. AND I have no sound! Tried all with Pulsaudio & ALSA, without Pulsaudio.... Sometimes I get an helping hand from a Ubuntu-specialist (even disabled) and to get answers from a Dutch Ubuntu-forum takes more time (if you get an answer as well!).

I'm a Windows-specialist (of the Commodore64/Atari-period) but never want back as free Windows-tester in all t ho se years (paid Microsoft software but never got service-support)

I hope somebody can help me in an understandable hight of CLI terminal textures to my age of 59

If all is working I'm very delight-full, thanks. Most of my words comes from a dictionary so it could be not the same English text as you learned it as well, sorry for that!

~ I'm open, honest and sincere to myself, to my partner and with some reticent also to others...! ~ 
#But never trust the US-intelligences#

don't know how to past in an apart window/screen here
eglefino@EglefinoPC:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:14.3 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers [8086:3438] (rev 13)
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.2 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 [8086:3a44]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] [1002:68b8]
02:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
04:00.0 SATA controller [0106]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 03)
04:00.1 IDE interface [0101]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 03)
05:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers [8086:2c41] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder [8086:2c01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Link 0 [8086:2c10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 [8086:2c11] (rev 05)
ff:03.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller [8086:2c18] (rev 05)
ff:03.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder [8086:2c19] (rev 05)
ff:03.4 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers [8086:2c1c] (rev 05)
ff:04.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers [8086:2c20] (rev 05)
ff:04.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers [8086:2c21] (rev 05)
ff:04.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers [8086:2c22] (rev 05)
ff:04.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2c23] (rev 05)
ff:05.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers [8086:2c28] (rev 05)
ff:05.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers [8086:2c29] (rev 05)
ff:05.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers [8086:2c2a] (rev 05)
ff:05.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2c2b] (rev 05)
ff:06.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers [8086:2c30] (rev 05)
ff:06.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers [8086:2c31] (rev 05)
ff:06.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers [8086:2c32] (rev 05)
ff:06.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers [8086:2c33] (rev 05)

---

### Post by TheFu on 2013-08-03
If you only communicate with systems on the internet, then 100base-T is as fast as most broadband connection anywhere in the world. Only GigE fibre connections in a few places can use anything faster - Google and some city internet systems do that - not Comcast, not AT*T, not ... pretty much anyone else.

OTOH, if you are networked inside your home with other PCs, then getting the GigE speeds can be VERY important. A few questions:
1) Are more than 1 PC in the house wired and connected with GigE?
2) Are all the ports in the router or switch GigE?
3) Are all the cables CAT5e or better?

It seems (I don't know for certain) that your new Comcast router is probably only 10/100 capable and auto-negotiated the connection speed for the computer.  That means everything is working as designed.  It doesn't do any good for 1 side of the cable to be faster than the other side is.  The specific Realtek chips you have are very well supported in Linux, so I can't imagine any driver issue at all.

The output of **ifconfig** might be helpful to see the connection speed.
The output of **sudo lshw -short -C  network** will be helpful.
It is best to only deal with 1 problem per thread here, so please stay with the network and open other threads for other issues.

I'm positive that your English is better than my Dutch!

---

