---
title: "nVidia Corporation MCP67 High Definition Audio"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by 2manydrugsago on 2008-02-02
i nought a new computer and  it has nVidia Corporation MCP67 High Definition Audio for sound. the ALSA drivers dont work. how can I fix this?

---

### Post by wolfen69 on 2008-02-02
try this [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by 2manydrugsago on 2008-02-02
This is what I get.

harlan@harlan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
harlan@harlan-desktop:~$ 
 
but my .avi  shows in totem don't have sound.  I cant use skype i can use XMMS to play music.
I did not understand most of the link you sent me. 
is there somthing else i can do?

---

### Post by 2manydrugsago on 2008-02-02
should I install the  64 bit distro?

---

### Post by dcstar on 2008-02-03
> **2manydrugsago said:**
> i nought a new computer and  it has nVidia Corporation MCP67 High Definition Audio for sound. the ALSA drivers dont work. how can I fix this?

The current 7.10 kernel may not support your new chipset, the next release (8.04) will have a later kernel that might have support for your hardware (I am waiting for my MB's sensors to be supported in this new release).

You can currently use the development releases of 8.04, but be aware that these are still under constant development and will be full of issues until the release date in April.

---

### Post by 2manydrugsago on 2008-02-03
so maybe  6.06 or 7.04 or the 64 bit might work? Id hate to have to go back to using Microcrap

---

### Post by sweetcancer on 2008-02-05
Try installing the linux-backports-modules and reboot. Worked for me with the same audio device

---

