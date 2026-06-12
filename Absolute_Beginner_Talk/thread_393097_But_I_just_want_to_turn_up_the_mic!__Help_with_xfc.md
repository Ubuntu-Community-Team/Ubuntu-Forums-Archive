---
title: "But I just want to turn up the mic!  Help with xfce4-mixer needed."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-03-25
My volume control panel on Xubuntu 6.10 (namely xfce4-mixer) offers the following sliders:
* Master
* Master-Mono
* CD Control-Center
* 3D Control-Depth
* PCM
* Line
* CD
* Mic
* Video
* Phone
* PC Speaker
* Aux
* Capture
... and switches:
* 3D Control Switch
* Mic Boost +20 dB
* Mix
* Mix Mono
* External Amplifier
... and drop-down menus:
* PCM Out Path & Mute (pre 3D, post 3D)
* Mic Select (Mic 1, Mic 2)
* Mono Output Select (Mix, Mic)
Where can I read up on what all this is supposed to mean?  Which widgets are relevant to me?
I just wanted to TURN UP THE MIC!:guitar:

---

### Post by thornomad on 2007-03-25
From the command line try running: alsamixer.  You could play with that.

---

### Post by ajgreeny on 2007-03-25
> **Blofeld said:**
> My volume control panel on Xubuntu 6.10 (namely xfce4-mixer) offers the following sliders:
* Master
* Master-Mono
* CD Control-Center
* 3D Control-Depth
* PCM
* Line
* CD
** * Mic**
* Video
* Phone
* PC Speaker
* Aux
* Capture
... and switches:
* 3D Control Switch
** * Mic Boost +20 dB**
* Mix
* Mix Mono
* External Amplifier
... and drop-down menus:
* PCM Out Path & Mute (pre 3D, post 3D)
** * Mic Select (Mic 1, Mic 2)**
* Mono Output Select (Mix, Mic)
Where can I read up on what all this is supposed to mean?  Which widgets are relevant to me?
I just wanted to TURN UP THE MIC!:guitar:

You need to make sure the mic is on using the sliders and any switch to make sure that it is live (you can't have the line in, CD, video or phone, if they are options, live at the same time) then try the 20dB boost.

---

### Post by Blofeld on 2007-03-26
Most helpful answers, thank you AJ and Nomad!:KS

---

### Post by aidanr on 2007-03-26
capture also affects the mic for me

---

