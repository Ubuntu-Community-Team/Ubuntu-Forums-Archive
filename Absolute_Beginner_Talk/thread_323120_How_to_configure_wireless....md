---
title: "How to configure wireless..."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Euphoric Invasion on 2006-12-21
Hey,

I am not sure if this needs to be in the begginer's section, so parden me if this sounds a bit.... dumb.

I recently got a generic wireless card (the kind that sits on the motherboard, not a USB dongle) and I don't even know if it recognized it. I got it to work with win98se, so I know the card is good. How do I get Edgy to work with it? I did all I know (which is not alot) with the network thing on the system menu, but it doesn't give me much options. Can anyone help me? I HAVE to have internet on this computer and it HAS to work with this card (its not my computer, I am just fixing it and I figured, since they don't care, Ubuntu would be better than win any day), but if I can't get it to work, I'm gonna have to go to windows  I REALLY don't want to if I don't have to :'( So I need help to get it working. I got everything else working, except the wireless   

Thank you in advance (for all those who help and all those who try)

-E.I.

---

### Post by PWill on 2006-12-21
First let's find out if it's recognized:
Open a terminal (Applications > Accessories > Terminal)

Then type in lspci
You should get a list of your PCI cards. Hopefully there will be one that says "Wireless Controller" or something of the sort. Copy and paste that back here, and then we'll move on.

---

### Post by Euphoric Invasion on 2006-12-22
Thanks, unfortunatly I have to do this at two different places.  The computer I'm working on is at my place, and I cant get the internet working there... so I have to alternate between 2 places.  I'll get you the information as fast as I can.

Thanks again.

---

### Post by Euphoric Invasion on 2006-12-23
Hey,
I did the *lspci* and this is what I remembered:
It is Texas Instruments. (OEM)
it is an IEEE card
Ubuntu does recognize it.  so thats good.
I had to do static IP b/c when I did *ifconfig* it did not show me an IP address on the wireless.  When I did static IP it showed the IP, but still no Internet.
I'll get the exact information from it once I go back to my place and copy the information (by hand :( )

Thank you very much for your help.

-EI

---

### Post by PWill on 2006-12-23
Ok, now that we know it's recognized, we have a few options. First, we need to find out the exact chipset, which we can get once you copy down the lspci information.
Then we will be able to determine if this card can be used with Linux kernel modules, or if we will need to use NDISwrapper, which uses the Windows drivers.

---

### Post by Euphoric Invasion on 2006-12-24
First of all, I read your comment and saw that it was possible to use windows drivers on Linux... I was, and still am, amazed at this!  This means that even if Linux does not support this driver, I can still stay away from windows. :D

Ok, I saved it on a diskette, and here it is....

$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
00:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
00:0d.0 Ethernet controller: Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem
00:0d.1 Computer telephony device: Broadcom Corporation BCM4212 v.90 56k modem
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

Thank youfor helping.

-EI

---

### Post by PWill on 2006-12-24
Which version of Ubuntu are you on? Dapper? Edgy?
Go to System > About Ubuntu to find out.

---

### Post by Euphoric Invasion on 2006-12-24
edgy 6.10
It was the ISO that was available about a week or so after Ubuntu 6.10 came out.

Thanks,

-EI

---

### Post by PWill on 2006-12-27
Try running these commands: 
1. ```
sudo ln -s -f /lib/firmware/`uname -r`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`uname -r`/acx/default/tiacx111c16
``` 
2. ```
sudo modprobe acx
```
3. ```
sudo ifup wlan0
```

4. And then try to configure your network card in System > Administration > Networking
(Or NetworkManager if you are using that...)
If that doesn't work, reboot your computer, and try step 4 again.

---

