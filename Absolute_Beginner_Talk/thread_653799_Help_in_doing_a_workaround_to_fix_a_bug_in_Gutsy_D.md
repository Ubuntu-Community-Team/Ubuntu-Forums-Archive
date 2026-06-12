---
title: "Help in doing a workaround to fix a bug in Gutsy Desktop"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by therudeboyd on 2007-12-30
I've yet to get sound working on my Acer 4220 laptop after installing Gutsy Deskop.  After much seraching I discovered a bug had been reported relating to sound and Gutsy for people using an intel HD card with a Realtek codec (268)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I can't follow the advice given as it assumes I'm not an idiot.  Please could someone write step by step pointers as to what I should do to get the bug solved so I can't get sound on my laptop and enjoy my life again. 

Thanks

---

### Post by spiderbatdad on 2007-12-30
i'll start by saying i'm no expert...looks like the first thing they want you to do is run```
lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` 

```  and ensure it matches pci id  8086:284b.   as this is the device affected by the  bug.

---

### Post by therudeboyd on 2007-12-30
00:07.0 0403: 10de:055c (rev a1)

????

---

### Post by spiderbatdad on 2007-12-30
10de:055c  is the relevant output. I'd say that doesn't match at al. There may just be some alsa settings to fiddle with. I think there is a package in synaptic for improving your user interface settings in alsa. Be patient and someone with more experience in this sound card problem will pick up the post and help you.:)

---

### Post by therudeboyd on 2007-12-30
> **spiderbatdad said:**
> 10de:055c  is the relevant output. I'd say that doesn't match at al. There may just be some alsa settings to fiddle with. I think there is a package in synaptic for improving your user interface settings in alsa. Be patient and someone with more experience in this sound card problem will pick up the post and help you.:)

 
Thanks for that. I'll give it another day to see if anything works but I've already spent 2 days trying to fix it and it's very frustrating. I've been through all the various documentation that there is but still no good.  I'm going to see if OSS is a better option than Alsa

---

### Post by spiderbatdad on 2007-12-30
you might try something simple like this too, but don't get carried away trying to install alsa drivers and the like...```
sudo apt-get update
sudo apt-get uprade
``` then go to synaptic and select the ubuntu supported alsa-utility. click it and select completely remove. Then click it and install it again. Reboot. Then go to the speaker icon in the panel and right click...open volume control...fiddle with settings...

---

### Post by therudeboyd on 2007-12-30
Thanks, I tried all that before and it didn't make it work any better.
Is it possible to use OSS and stop ALSA from working, If so how do I go about it.

---

### Post by spiderbatdad on 2007-12-30
Anyone else have input...?

---

