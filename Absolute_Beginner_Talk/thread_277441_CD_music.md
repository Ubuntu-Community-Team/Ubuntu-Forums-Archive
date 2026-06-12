---
title: "CD music"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Alvar on 2006-10-14
I put in my cd and the program opens to play the cd, but I can't hear anything. I checked if it is muted and it is not. PLZ HELP

---

### Post by taurus on 2006-10-14
Do you have sound at all when the login screen comes up (drum beats)?  Also, do you hear sound from your speakers when you log in?

---

### Post by Alvar on 2006-10-14
Not a sound when I boot up. nothing,

---

### Post by taurus on 2006-10-14
> **Alvar said:**
> Not a sound when I boot up. nothing,
Then perhaps your soundcard is not working!  What kind of soundcard do you have and the manufacture/model of it?  Is it a PCI or an onboard?

---

### Post by Kateikyoushi on 2006-10-14
Follow this guide to install your sound card. Start at the general help section.
[Sound guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

### Post by Alvar on 2006-10-14
Well i checked and it says "Intel 82801DB-ICH4" and i'm using a laptop, so most likely onboard.

---

### Post by NeoLithium on 2006-10-14
In a terminal window, run alsamixer, and ensure that nothing is muted; sometimes a certain aspect may have it's volume way down, or muted; and therefore you can't hear anything.  I know on mine, when I install, it defaults with my VIA sound control muted, and I can't hear anything until I physically turn it up.

---

### Post by Kateikyoushi on 2006-10-14
I have the same in my notebook.

In alsamixer i had to mute external amplifier and headphone jack sense off to get sound from the built in speaker.

---

### Post by Alvar on 2006-10-14
Alsamixer didn't help, this is getting frustrating

---

### Post by taurus on 2006-10-14
Let's see if the system even sees your soundcard.  What's the output of this command from a terminal then?

```
lspci
```

---

### Post by Kateikyoushi on 2006-10-14
Please copy this to a terminal what's the output ?

```
aplay -l
```

---

### Post by Alvar on 2006-10-14
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Alvar on 2006-10-14
thats what it gives me

---

### Post by Alvar on 2006-10-14
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Kateikyoushi on 2006-10-14
That looks like an lspci.

Ah okay, the second one is fine.

You sound card is detected and the module is loaded.

You have to play with alsamixer to get it working.


Try to mute the external amplifier and see if it gets going also try it with headphone because if the headphone jack sense was not muted my built in speakers did not work.

---

### Post by Alvar on 2006-10-14
The first one is lspci
the second one is a-play

---

### Post by taurus on 2006-10-14
Again, play around with the options in alsamixer and don't forget to check the volume on your laptop as well with the "F" function as well...

---

### Post by Alvar on 2006-10-14
I'm sorry but what is the "f" function?

---

### Post by taurus on 2006-10-14
> **Alvar said:**
> I'm sorry but what is the "f" function?

The blue keypad on your keyboard where you hold own to increase/decrease/mute the volume of your speakers!!!  What model is your laptop anyway?

---

### Post by Alvar on 2006-10-14
It's the gateway 7330 type

---

