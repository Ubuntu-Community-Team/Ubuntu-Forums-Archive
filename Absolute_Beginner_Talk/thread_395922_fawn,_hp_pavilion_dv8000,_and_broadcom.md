---
title: "fawn, hp pavilion dv8000, and broadcom"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by derekx on 2007-03-28
I'm trying Ubuntu again. I gave up the first time for a lot of reasons but have been really wanting to give it another shot. When I saw the beta for fawn out I jumped on it ( and i like it alot, much easier than than edgy btw ) 

I have two main goals:

1. get wireless working 
2. get beryl

From what I have read it seems I have both the worst possible wireless networking card:

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

and the worst video card:

ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

I tried so many things on the forums and elsewhere to get the wireless working under 
edgy and nothing worked. I must have tried 10+ methods.

So I guess what I need to know is has anyone got this wireless card working? and can they point to an EASY to understand tutorial for me to do it. I'm a super linux noob.

As with the video card is it doomed for ever running beryl and xgl well?

I'm running the 64bit version and would like to keep it that way if possible.

Heres my lspci if that helps:

Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
PCI bridge: ATI Technologies Inc RS480 PCI Bridge
 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



Everything else seems to work very well. Thanks for any help.

---

### Post by lamalex on 2007-03-28
I have the same graphics chipset and i was able to get the built in desktop effects in literally 3 clicks, enable restricted drivers, restart, enable desktop effects. it worked just like that. as for wireless have you tried ndiswrapper? Last i heard the bcm43xx drivers didnt work with that card but idk, i have bcm4311 which just worked with apt-get install bcm43xx-fwcutter and it did all of the work for me!

---

### Post by derekx on 2007-03-28
What is apt-get? I tried in the add/remome programs thing and it didnt find it.
I did however find it on the web and am trying that out now. 

In edgy I tried the ndswrapper but had no luck I havent tried in fawn yet because I wanted some feed back first.

About the driver from the "restricted drivers manager" but when I try "desktop effects"
I get an error message stating the core extension is not available. 

Hopefully i'll have better luck with xgl and beryl.

---

### Post by derekx on 2007-03-28
OK, that got the wireless working. It only is using wireless "b" speeds however but its a great improvement and I'm not complaining. :KS 

Thanks for the assistance. What's the deal with the keyring manager btw?

And for my last issue has anyone had good success with Beryl and XGL with the ATI 200m?

---

