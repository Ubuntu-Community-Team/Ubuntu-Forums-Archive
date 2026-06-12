---
title: "Can't get my USB Mic (Logitech) to work!"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-05-01
I have that desktop mic from logitech and I can't get it to work.  I tried messing with the audio settings but that did not get me anywhere.  I can see that on the device list it says "usb audio", but it still doesn't record anything when I select it.

---

### Post by lepz on 2007-05-01
I dont have the mic your talking about, but have you tried the volume control "preferences" settings.

---

### Post by zidkenu on 2008-07-07
Logitech USB Desktop Microphone Ubuntu 7.04
--Volume Settings:
Right click on VolumeCtrl-> OpenVolumeControl:
switch all on and to MAX for...
File-> Change Device-> HDA ATI SB (Alsa mixer)
File-> Change Device-> AK5370 (Alsa mixer)

--Do Device Recognition Test and Device Driver Test
[http://www.daniel-lemire.com/blog/archives/2005/10/12/logitech-usb-desktop-microphone-under-linux/](http://www.daniel-lemire.com/blog/archives/2005/10/12/logitech-usb-desktop-microphone-under-linux/)

--Choose correct sound card for sound capture:
[https://www.sk3ptik.net/blog/?p=47](https://www.sk3ptik.net/blog/?p=47)
(because the USB Microphone itself is a little sound card)
Notice the typo at the line: "cat /proc/asounds/cards"
it should be "cat /proc/asound/cards", no "s" after asound

--Skype Test
In Skype: Tools-> Options-> Sound Devices-> Audio In=AK5370
Call Skype Testing Service, for example: echo123
--
Sometimes after reboot, the microphone input level is zero! Max it!
In Skype-> Options-> Sound Devices,
Uncheck "Allow Skype to automatically adjust my mixer levels"

---

