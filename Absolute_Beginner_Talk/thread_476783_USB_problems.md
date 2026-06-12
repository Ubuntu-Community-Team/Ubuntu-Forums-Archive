---
title: "USB problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by nihuacatelco on 2007-06-17
I just installed Ubuntu on my laptop and i'm having some problems with my usb mouse and external hard drive. When i restart the computer they will work, but once I use either of them they both stop working shortly.

I tried using lsusb command to see if they were connected and they do show up untill I try using any one of them and afterwards they will disconnect, and switching ports does not restart them.

---

### Post by w4ett on 2007-06-17
Do you have them plugged into a hub or directly into the machine?

---

### Post by nihuacatelco on 2007-06-17
They are plugged into separate ports. No USB hub.

---

### Post by w4ett on 2007-06-17
Apart from a motherboard/Power supply problem, I can't think of any reason for them to 'Stop" working.   

Please post the output of:    lspci

and:  lsusb

This will give us the particular chipset on your motherboard/cards.....I'm also wondering if there might be a heat issue with your system. You might want to check the temps on your cpu and motherboard too.... Just trying to troubleshoot...I'm a hardware guy at heart?!?!?

---

### Post by nihuacatelco on 2007-06-17
Thanks for helping out

I have had problems with overheating, but its never prevented me from using multiple USB peripherals at once.

After messing around more with the usb ports, the external hard drive will work, but when i plug in a mouse as long as i don't move it, the external hard drive keeps working, but when i try using it the hard drive and the mouse both stop working about 10-15 seconds after that. I tried with 2 different USB mouses too.

The output from lspci

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

Output from lsusb

Bus 003 Device 002: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 001: ID 0000:0000

---

### Post by w4ett on 2007-06-17
the more you tell me, the more it sounds like a hardware issue.   Do you have a USB extension cable available?  If you do...try using it to reposition your wireless mouse receiver unit away from the Computer Case and the hard drive and also to reduce movement on the USB Bus plug..  if you have  a USB plug on the front of the case use it  so we can try and rule out the actual USB Plugs/Connectors and wiring.

---

### Post by nihuacatelco on 2007-06-19
I'm using a usb hub now to connect the mouse and the hard drive, both work now, however, the cursor lags when I use the usb mouse, and does not lag when i'm using the touchpad. Any Idea  what is causing that lag?

---

