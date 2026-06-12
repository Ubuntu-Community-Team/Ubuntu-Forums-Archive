---
title: "Wireless Problems HP dv5000"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by nina_aoki on 2008-04-15
Hello --

I've recently inherited an HP dv5000 notebook and of course loaded Ubuntu on it.  I'm having issues with the internal wireless card.

When I first installed Ubuntu (7.10) I was able to see my WiFi network and connect to it.  I thought I got away clean here...

However, upon reboot and subsequent attempts -- I cannot connect to my network.

I can see the network and every other WiFi network in my neighborhood but I cannot connect.  Could anyone please point me in the right direction to get this working?  I'm fairly new to Ubuntu and Linux and some of my questions are definitely going to be n00b type.

Here is the output I get from checking the system:

nina@nina-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
nina@nina-laptop:~$ 


It looks like the card is a Broadcom BCM4318 -- but what to do now is a mystery to me.

Thanks much,

- nina

---

### Post by Inxsible on 2008-04-15
If you can see the networks around you, your wireless is working fine. Have you tried creating a new network and then supplying the SSID of your network along with the password. Sometimes you also have to create a network manually and then try.

---

### Post by nina_aoki on 2008-04-15
@Inxsible

Really?  Okay - I'll try that.  

So - I should try and configure the network manually then.  What I'm seeing is the SSID of all of the WiFi networks in my area - when I attempt to connect I see the "green circle" in the upper right corner.  One light illuminates the other is dark.  The I get a prompt to enter my network key (64 Bit Hex)  -- it then tries to connect and then comes back and asks me for the network key again -- but it never manages to connect.

There's actually someone in my neighborhood with an open network which I tried to connect to and got the same result.

So - I will try that.  

I've just read a lot of threads about problems with the Broadcom chipset and I didn't know if I needed to do something different?  I have the restricted Broadcom driver enabled and as I said, I was able to connect to my WiFi network when I first installed Ubuntu - but nothing since.

Thanks for the tip - I'll come back and advise!  (I hope it works!)

Thanks much!   ;)

- nina

---

### Post by Inxsible on 2008-04-15
> **nina_aoki said:**
> ..... when I attempt to connect I see the "green circle" in the upper right corner.  One light illuminates the other is dark.  The I get a prompt to enter my network key (64 Bit Hex)  -- it then tries to connect and then comes back and asks me for the network key again -- but it never manages to connect.- ninaGreen circles are good :)

Are you sure you are entering the correct keyring manager password?

---

### Post by nina_aoki on 2008-04-26
Yes!  Green circles are good!  lol!

> Are you sure you are entering the correct keyring manager password?

Yep! ;)

I actually waited for Hardy to be released.  This notebook I was working with was a side project -- and as I expected, when I installed Hardy my wireless issues cleared right up. Yay! 

The Broadcom restricted driver was installed and everything worked perfectly.  

So this makes two machines I've converted to Ubuntu.

- nina


***OnEdit: ** Okay - how do we mark threads as SOLVED now?  I don't see this menu option anymore.*

---

