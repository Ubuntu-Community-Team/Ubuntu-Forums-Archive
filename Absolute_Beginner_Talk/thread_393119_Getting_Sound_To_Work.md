---
title: "Getting Sound To Work"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Bungo Pony on 2007-03-25
My PC has onboard sound, but it doesn't work in Ubuntu. I downloaded the Linux drivers from the manufacturer, but I'm completely lost beyond that point.

How do you install drivers?

---

### Post by r4ik on 2007-03-25
Try,

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by Bungo Pony on 2007-03-25
I went through that with no such luck. There is no ALSA driver for my onboard sound card :(

Check it out:

 sudo modprobe snd-
FATAL: Module snd_ not found.

---

### Post by r4ik on 2007-03-25
What soundcard do you have ?

---

### Post by Bungo Pony on 2007-03-25
It's onboard sound made by RealTek

---

### Post by r4ik on 2007-03-25
Please post again here ran out of ammo,

[http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138)

sorry.

---

### Post by kipriano on 2007-03-25
Big problem. i installed the alsa driver for my soundcard: realtek ac97 so i could play sound in surround, but now it doesn't work at all. what should i do? help please

---

### Post by r4ik on 2007-03-25
> **kipriano said:**
> Big problem. i installed the alsa driver for my soundcard: realtek ac97 so i could play sound in surround, but now it doesn't work at all. what should i do? help please

Start an own thread please.

---

### Post by Bungo Pony on 2007-03-25
Got it to work! I followed the directions here and it went flawlessly:

[http://www.ubuntuforums.org/showthread.php?t=390625&highlight=realtek+sound](http://www.ubuntuforums.org/showthread.php?t=390625&highlight=realtek+sound)

---

### Post by r4ik on 2007-03-25
Congrats !
Help someone with the same prob one day :)

---

