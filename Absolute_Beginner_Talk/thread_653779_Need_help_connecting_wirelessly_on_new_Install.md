---
title: "Need help connecting wirelessly on new Install"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2007-12-30
I just added Ubuntu 7.10 to my Dell E1705 laptop. The network card is a "Dell 1390 WLAN minicard" that was pre-installed when I bought the computer new from Dell.

Connecting with Vista is no problem, but I have not been able to connect from Ubuntu. 

What do I need to do to connect?  from the looks of it, the computer doesn't even see a network.

---

### Post by rich.bradshaw on 2007-12-30
Try running the Restricted Drivers Manager in the system/admin menu.

Do this with your laptop plugged into your router with an ethernet cable, as it needs to download files from the internet.

---

### Post by parts-man73 on 2007-12-30
Trying that now....

I get a message "The software source for this package - BCM43xx - fwcutter is not available"

---

### Post by doorknob60 on 2007-12-30
ooh...it's a broadcom...that could be annoying. I found a good guide on the web before but can't find it again, just google it and eventually it should work.

---

### Post by slibuntu on 2007-12-30
> **doorknob60 said:**
> ooh...it's a broadcom...

Basically means you've got a challenge on your hands!   :)

---

### Post by anewguy on 2007-12-30
Yes, Broadcom drivers can be a challenge, but hey - let's try to get this thing working.  The first thing I would like you to do is the following:

(in a terminal window:  Applications/Accessories/Terminal):

lspci


Copy and paste the output of that back here and we'll go from there.

:)

---

### Post by parts-man73 on 2007-12-30
Thank you for your offer of help! Here is what I get...

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


---

### Post by anewguy on 2007-12-31
Rather than repeat what's already been posted, I thought I would direct you to the following link.  While it is for a different brand of laptop, it is for the same wireless card which is all you need to worry about.  I tried to help this individual and the information you need is on the 3rd page of the posting.

[http://ubuntuforums.org/showthread.php?t=639589&page=3]("http://ubuntuforums.org/showthread.php?t=639589&page=3")

Please post back if you have any question or problems!!:)

---

### Post by parts-man73 on 2007-12-31
An excellent link, I'll try that when I get home from work tonight. Thank you for your invaluable help.

I wonder if I might ask you 1 more networking question. 

When I plugged the laptop directly into my router, The internet worked, but it was very sluggish. But any other computer on the same network performed as normal. In fact, when I booted back into windows on the same machine, the internet zipped along as normal.

Any idea what could slow it down like that?

Thanks again for your help,
Brian

---

### Post by parts-man73 on 2007-12-31
I might have found the answer to that question here

[http://ubuntuforums.org/showthread.php?t=653854&highlight=IPV6]("http://ubuntuforums.org/showthread.php?t=653854&highlight=IPV6")

but thank you again for your help

---

### Post by anewguy on 2007-12-31
Not sure on your connection speed unless indeed it was just the server you connected to.  Did the link help you get your wireless going?:)

---

### Post by parts-man73 on 2008-01-02
@ anewguy:

That got my wireless going, thank you for taking the time to help me there.

As for the slow speeds in firefox - here's the solution I found, and it worked. 

[LIST]
[*]type "about:config" in the address bar of firefox
[*]find the entry for IPV6 and click on it to change the boolean value to "False"
[*]restart Firefox
[/LIST]

and the internet is back to normal speed

---

