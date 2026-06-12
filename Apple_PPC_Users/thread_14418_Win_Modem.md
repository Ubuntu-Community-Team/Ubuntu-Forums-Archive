---
title: "Win Modem"
date: 2005-02-07
forum: Apple PPC Users
---

### Post by michelem on 2005-02-07
Hi,
someone can tell me what's a win-modem? I have an internal modem but ubuntu doesn't find it... :sad: 

Bye.

---

### Post by hashimoto on 2005-02-07
So then you most likely have a winmodem which needs software to control its function. If you know the make and model, it is possible that someone here may help you.

You can find more info on modems e.g. form here: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Modem-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Modem-HOWTO.html)

BR
Hashimoto

---

### Post by michelem on 2005-02-08
[QUOTE=hashimoto]So then you most likely have a winmodem which needs software to control its function. If you know the make and model, it is possible that someone here may help you.

You can find more info on modems e.g. form here: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Modem-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Modem-HOWTO.html)

BR
Hashimoto[/QUOTE]
 Hi,
thank you for your reply, i know the make and model of modem...i have done from ubuntu shell this comand: (lspci -v) that showed me all devices on computer and details of modem are these:

0000:00:10.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01) (prog-if 00 [8250])
Subsystem: Aztech System Ltd Packard Bell MDP3858V-E
Flags: medium devsel, IRQ 5
Memory at ee020000 (32-bit, non-prefetchable)
Capabilities: [40] Power Management version 1

Initially i tryed to go in "Application" -> "Networking" and add modem and set on ttyS0 or ttyS1...or ttyS4 but pc doesn't find it.
If you can help me what i have to do? Have i to configure a particular file or install a particolar application? I don't know....

Bye.
Michele

---

### Post by landotter on 2005-02-08
[QUOTE=michelem]
 HCF 56k[/QUOTE]

you should be able to use a proprietary driver from Linuxant. I'm not sure of the installation procedure for Debian, but I'm pretty sure you'll have to have your kernel source installed first.

I used to use their driver with Mandrake and Fedora. Despite all of the negative talk of winmodems--mine w/ the linuxant drivers was much more reliable than any external modem I've ever used.

The drivers are 15USD though, and for that kind of money you could get an external modem on ebay...

---

### Post by az on 2005-02-08
Is there a Powermac version of the driver?  It is a precompiled module made for i386.

---

### Post by Viro on 2005-02-09
[QUOTE=azz]Is there a Powermac version of the driver?  It is a precompiled module made for i386.[/QUOTE]
 It should be on the Linuxant site. I've seen it there before.

---

### Post by hashimoto on 2005-02-09
Rockwells modem is a winmodem and needs, as mentioned here, the Linuxant driver. Some discussion has been going on in this forum about that. Do a search for more information.

BR
Hashimoto

---

### Post by chele on 2005-02-09
I built and tried the HCF modem module on this powerbook 550. It crashed the computer hard. Apparently there is a conflict between the "modem" and the sound card. I emailed linux ant, they said they ae working on it. You are probably just better off with a real hardware modem. To bad apple is too cheap to include one, it would of only cost them 5$ or so. Bastards. 

Much better not to count on a closed-source 3rd party for this functionality. Get a modem supported by normal Linux kernels.

See [http://ubuntuforums.org/showthread.php?t=13443](http://ubuntuforums.org/showthread.php?t=13443)

---

