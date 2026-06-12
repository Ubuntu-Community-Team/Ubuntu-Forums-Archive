---
title: "[SOLVED] how do I enable my on board sound card?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2008-02-24
Here's a brief history of my problem:
I run dual boot XP & Ubuntu 7.10 but my on board sound card did not work properly on windows, so I bought a new one  (Creative Labs SB Audigy LS). Now everything is ok on Windows but there is no sound on Ubuntu. I have read that there are no linux drivers for this particular card but I can't see why  my on board card stopped working as well.
How do I choose the on board card and have ubuntu consider it as the default audio card?
Please help!!!! (if I knew something like that would happen, I wouldn't want any sound on windows in the first place! lol)

lspci gives the following:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
04:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:01.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
root@christina-desktop:/home/christina#

---

### Post by wolfen69 on 2008-02-24
go into bios.
go to integrated preipherals(or similar) and enable on board sound.

---

### Post by forestpixie on 2008-02-24
have you made sure that the analog/didgital switch is off - also check that the controls are up in alsamixer - I had problems until I realised that front had an effect

---

### Post by christina_svats on 2008-02-24
everything seems fine in bios, I didn't change anything there anyway...can you get something out of my lspci?

---

### Post by christina_svats on 2008-02-24
sorry, where is that analog/digital switch? what are the controlers analog f, g and r in alsamixer? everything is up there...
(forgive my ignorance)

---

### Post by forestpixie on 2008-02-24
dbl clk the volume icon in the top panel see if you have a switches tab

---

### Post by christina_svats on 2008-02-24
ok, I can choose between three devices: CA0106 (Alsa mixer), HDA Intel (which I guess is the on board card) and mixer00 (oss mixer). The first one has a switches tab and only one tickbox labeled IEC958. The HDA Intel has a switches tab as well with a tickbox labeled Headphone.

---

### Post by forestpixie on 2008-02-24
choose the alsa mixer - go to preferences - go down list see if there's a analog/digital jack channel, tick if there is and close - then there should be a switch for it make sure it's off

this will only help if the card has the jack physically obviously, it's just the first thing I had a problem with

might be a problem having the onboard sound on as well though

might help, might not - all you can do is see

---

### Post by christina_svats on 2008-02-24
sorry, no luck, there is only an analog center...
here's a screenshot of alsa mixer, if it helps...

---

### Post by forestpixie on 2008-02-24
are you using the optical input/output

if the IEC958 is ticked - untick it, adn see if that helps otherwise I can't help I'm afraid

---

### Post by christina_svats on 2008-02-24
Consider this!
It turns out that the problem had nothing to do with me having two audio cards...Instead, it was caused by an update, but this never crossed my mind...The solution came here from XVII:

[http://ubuntuforums.org/showthread.php?t=703376](http://ubuntuforums.org/showthread.php?t=703376)

Thank you forestpixie and wolfen69 for the attention! :KS

---

