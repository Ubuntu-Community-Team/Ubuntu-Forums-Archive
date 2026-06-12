---
title: "Sounds issues on 7.04 HELP!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Lordcoca on 2007-04-29
Running a Toshiba A135-s4427 laptop, here's the output of aplay-l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I still have no sound after trying the following:

Reinstalling Ubuntu

Tried all the advice in this thread: [http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

and alsamixer shows that nothing is muted


Any further advice for me? I'm not that tech savvy so explain what to try in layman's terms :)

---

### Post by Lordcoca on 2007-04-29
Should I try downgrading to Edgy? What features do I lose if I do that?

---

### Post by orb9220 on 2007-04-29
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

### Post by zerosystem on 2007-04-29
Also, keep in mind that for some reason Feisty has digital output enabled by default so you might want to change that by right clicking on the volume icon, clicking on 'open volume control', going to the switches tab, and unchecking the box that says digital output.

---

### Post by orb9220 on 2007-04-29
Not true for everone.

Mine is on board intel 82801BA-ICH2 alsa uing AC'97 and it does not have a "Switches Tab" only playback.

---

### Post by Hackza on 2007-04-29
I only get headphones tick box option in my switches tab.
My sound problems were solved by going into alsamixer and made the surround sound output max. Thought I'd just chip that in randomly

---

### Post by Lordcoca on 2007-04-30
> **orb9220 said:**
> [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

All that advises me to do (given my situation) is run alsamixer, it doesn't say what I should do if alsamixer doesn't fix the problem.

---

