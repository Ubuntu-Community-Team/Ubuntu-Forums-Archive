---
title: "Brand New, and problems with onboard sound"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Grenade on 2007-03-07
hi. i just installed ubuntu, everything seems to be working great except the sound. I have my drivers for my Asus p5VDC-x motherboard installed correctly i believe. @ first i had problems with finding compiler, but not now; it basically says that when i try to ./configure my alsa-libs and utils(after correctly doing the alsa-drivers with no problems) that i already have newer versions. (however the volume still shows me no gstreamer plugins/device available.) which takes me to the packages... when i look in synaptic package manager i can see the newer versions of alsa-base & alsa-utils both v1.0.11 installed. also i see gstreamer .10 with most all plugins installed already. so i decide to get rid of alsa-base and alsa-utils and see if i can't install the older versions then (v1.0.10rc2 from asus). the problem with that is the base wants to also remove "ubuntu-minimal" and the utils wants to also remove a bunch of gnome/nautilus stuff. from what i can tell this is not normal?? this is like my third day so forgive me if i didn't give All the proper information. thanks for any help guys!

---

### Post by 67GTA on 2007-03-07
Not to be too simplistic but did you check to see ifthe sound was muted? Check the sound icon on the panel.

---

### Post by Grenade on 2007-03-07
> **67GTA said:**
> Not to be too simplistic but did you check to see ifthe sound was muted? Check the sound icon on the panel.
yea i can't access that i guess because when i click on volume it says no gstreamer plugin/device found.

---

### Post by 67GTA on 2007-03-07
Go to SYSTEM>PREFERENCES>SOUND. Cilck the sound tab and look at the bottom of the window and see if there is more than one sound card listed under the default sound card button.

---

### Post by Grenade on 2007-03-07
> **67GTA said:**
> Go to SYSTEM>PREFERENCES>SOUND. Cilck the sound tab and look at the bottom of the window and see if there is more than one sound card listed under the default sound card button.
yes i have ALSA (which si what asus give drivers for) ESD and also OSS. if it helps my chipset i figured out is RTL8201CL but when i do a sudo modprobe snd-82xx it says no sound card foudn or whatever
edit: oh sorry and under the sounds tab there is no device whatsoever under "default sound card"
edit2: i thoguth it was rtl82xx by the chip but aparently my motherboard book says ADI ad1986A, problem is i can't find it on the [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) website, but asus has alsa drivers for it? i am stuck and don't kwno what to do!
edit3: sry so many edits but i did find it is' ANALOG DEVICES is the brand or whatever, but still the drivers on that site only go up to 1985 not the 1986a i have... so does that mean this version of ubuntu just doesn't work with my card period!?

---

