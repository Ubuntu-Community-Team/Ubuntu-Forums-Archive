---
title: "graphics and wireless card drivers"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Andygal on 2007-02-11
I have a D-Link AirPremier DWL-AG530 Wireless PCI Adaptar and a Radeon X800 GTO graphics card (dxdiag says chipset is  Radeon X800 GTO (Ox554F)).

I'm planning on dual-booting Windows and Ubuntu and I wanna know where I find the right drivers and what I do with them, since if my network card doesn't work I won't be able to get online in Ubuntu, do I download them under Windows and stick them on a CD-ROM or what).

This is an incredibly stupid question I know. I'm just trying not to give my computer any opportunity to give me **** and making sure I have everything I need before I start messing with my computer, and I've never used any OS other then Windows.

---

### Post by nickoli_02 on 2007-02-12
Since you have an ATI card, download the alternate install CD. This will give you the text based install since the driver that xorg loads by default won't work for ATI cards. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=359034]("http://www.ubuntuforums.org/showthread.php?t=359034")

As for installing drivers and such, is it possible for you to use a wired connection for your laptop temporarily? That would make things easier if drivers for your wireless card are not supported natively. To find out if your card is supported, search the forums for a list of supported cards, I know there's one around here somewhere.

---

### Post by Andygal on 2007-02-12
I'm on a desktop, and I can't use a wired connection because that would require drilling holes in walls which the landlord would not like :P.

And I'm getting conflicting reports from various places as to whether my card will work. One site says it will another site says it needs "fixing" because of some broken code or other.

---

### Post by nickoli_02 on 2007-02-12
Well, that's unfortunate... if the correct driver for your card is packaged with the ubuntu CD then you should have minimal troubles getting it configured. I'll do some research on the wireless card for you, there's most likely a guide around here somewhere

---

### Post by nickoli_02 on 2007-02-12
Your wireless card uses the Atheros chipset, which is supported by the madwifi wireless driver. You can download the madwifi driver from [here]("http://www.madwifi.net/"). Welcome to linux!

---

