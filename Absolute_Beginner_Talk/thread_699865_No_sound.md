---
title: "No sound"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by cane1832 on 2008-02-17
Ok anyones help greatly appreciated

I have the compaq c715nr laptop and i have the intel hda sound card
now my sound was working until i tried fixing the problem with the headphones and the speakers outputting at the same time. Now my sound doesn't work at all and im totally lost.
When searching for the solution to the problem with the headphones i found a post that said run this command

sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders

then i rebooted and now no sound at all.....man this sux

 :mad:

---

### Post by herbster on 2008-02-17
Have you opened alsamixer and checked the volume levels? Appears you've reinstalled/upgraded Alsa, so the alsamixer might be set at mute, the default level when installed. You can also try apt-get install gnome-alsamixer.

---

### Post by cane1832 on 2008-02-17
Ok got the sound back working but no cut out of speakers when i hook up the headphones
sound outputs on both anyone got any ideas

---

### Post by herbster on 2008-02-17
USB or stereo headphones?

---

### Post by cane1832 on 2008-02-17
stereo

---

### Post by herbster on 2008-02-17
Try the last post here: [http://ubuntuforums.org/showpost.php?p=4233766&postcount=10](http://ubuntuforums.org/showpost.php?p=4233766&postcount=10)

---

### Post by cane1832 on 2008-02-17
off hook doesn't appear

---

### Post by herbster on 2008-02-18
What do you see in volume control? When you hit ALT+F2 and type "gnome-volume-control", click Edit> Preferences and check all the boxes. Do you see "Jack" or "Jack sense" or anything? Please list the options you see.

---

### Post by cane1832 on 2008-02-18
The only boxes that are availible to check are master, pcm, capture, and digital. 
hope that helps and thanks for you help

---

### Post by cane1832 on 2008-02-18
bump

---

### Post by Hobo Joe on 2008-02-18
Paste the output of:
```

sudo asoundconf list

```

---

### Post by cane1832 on 2008-02-19
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel


thats what it gives me in return to that command

---

### Post by northern lights on 2008-02-19
Maybe try to post```
cat /proc/asound/cards
``` and ```
cat /etc/asound.conf
``` instead

---

### Post by cane1832 on 2008-02-19
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x92400000 irq 23

the other command doesn't work

---

### Post by northern lights on 2008-02-19
Gee - I've posted this somewhere else no ten minutes ago - the problem is your sound device, which is apparently widespread hardware. The following HowTo should solve your problem: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by northern lights on 2008-02-19
Gee - I've posted this somewhere else no ten minutes ago - the problem is your sound device, which is apparently widespread hardware. The following [Howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") should solve your problem, else, this [thread]("http://ubuntuforums.org/showthread.php?t=314383") could also prove helpful.

[EDIT]Darn, I meant to edit my first post not reply anew - anyway to delete my own posts?[/EDIT]

---

### Post by Hobo Joe on 2008-02-19
Run this command:
```

sudo asoundconf set-default-card Intel

```

---

