---
title: "usb logitech headset setup?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by KeitaroCoS on 2007-07-25
Hey everyone, I have a logitech USB headset, and I can't seem to get it working, I've looked through all the similar threads, but none of the things worked, anyone know how to get this thing working?

---

### Post by KeitaroCoS on 2007-07-25
ker-bump! ohez yeah! help me out please

---

### Post by jcconnor on 2007-08-25
You may want to try the stuff from this thread:

[http://ubuntuforums.org/showthread.php?t=508123&highlight=best+usb+headset]("http://ubuntuforums.org/showthread.php?t=508123&highlight=best+usb+headset")

John

---

### Post by downgrade on 2007-08-25
Huh, I bought one recently too, all I did was plugged it in and it worked, but mines weird, playing mp3s goes through my computers speakers, playing computer games goes through the headset.

---

### Post by leafw on 2007-08-28
The two sound outputs can be configured under System / Preferences / Sound
so that one can keep audoconferencing separate.

The Logitech USB headset just works here (ubuntu 7.04 in a Thinkpad T60).
For the latest skype to work properly, though, I had to launch it like this:

$ esd -d /dev/dsp1
$ esddsp /usr/bin/skype


Using the System / Preferences / Menus, you can set the above in the launcher like this:

esddsp /usr/bin/skype

Be sure to launch the esd -d /dev/dsp1 from some terminal after plugging in the headset, and before launching skype. It all use to work just fine without any tweaking before the last skype .deb package upgrade. Hopefully it'll be fixed for 7.10 gutsy.

Hope it helped.

---

