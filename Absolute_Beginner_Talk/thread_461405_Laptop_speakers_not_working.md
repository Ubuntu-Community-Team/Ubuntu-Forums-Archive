---
title: "Laptop speakers not working?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-06-01
I just install edgy on my brothers laptop (I'm slowly converting everyone I know from MS garbage). All of the audio drivers should have been installed properly, but no sound comes out of his speakers. Any ideas on where to start?

---

### Post by ugm6hr on 2007-06-01
Do headphones work?  If yes - you need to edit the alsamixer settings.  Best to let us know what hardware he has (maybe lspci output).

---

### Post by HgBoy on 2007-06-01
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


Don't have any headphones handy right now. It is a gateway laptop with mostly intel hardware.

---

### Post by brian.freelancer on 2007-06-01
This might sound dumb but it worked for me.

Double click on the speaker icon and see max out all the sliders there. Make sure nothing's muted. Had this same problem with my Aspire 5570, turns out the "surround" slider controls the output to the laptop speakers. :)

---

### Post by annda on 2007-06-01
it *should* work. try alsamixer in the terminal and unmute everything ('m' key).

---

### Post by HgBoy on 2007-06-01
I have everything turned up. I'm not seeing a "surround" option though. Just pc speakers, master, cd, line-in, mic.

---

### Post by annda on 2007-06-01
as brian says, you can try sound settings in gnome - enable all the options in preferences and try the switches - they are different for every card, so surround may be your culprit.

---

### Post by HgBoy on 2007-06-01
still nothing. I'm confused. Is there any way too see if the speakers themselves are connected.

---

### Post by ugm6hr on 2007-06-01
> **HgBoy said:**
> I have everything turned up. I'm not seeing a "surround" option though. Just pc speakers, master, cd, line-in, mic.

Did you do it from Terminal:
alsamixer

Left/right & up/down to move between options.  "M" to change from mute (MM) to on (OO).

There should be loads more options if you keep pushing right arrow key.

---

### Post by m2montazari on 2007-08-08
hi
you should simply download and install alsamixer and maybe alsa... and install them.
then you would see gnome alsa mixer or sth like this in application>sound and video>
open it and unmute all specifiecly Surround.
i had tried this and im sure you would success too.

---

### Post by larsemil on 2007-08-12
well i have the same problem, same soundcard,  allthough my speakers are working every now and then. but i do have a problem that i need to reboot to get that sound sometimes and that is disturbing. 
and i have been going over this a couple of times and NO its not about wrong alsamixersettings. it is something else.

---

### Post by HgBoy on 2007-08-13
If it is the same soundcard, I managed to fix the problem by installing the sl-modem-daemon and sl-modem packages in synaptic. Apparently, at least in my situation, the soundcard is tied into the darware portion of the modem. Install those and it should say something about new devices being detected, and the speakers should work.

---

