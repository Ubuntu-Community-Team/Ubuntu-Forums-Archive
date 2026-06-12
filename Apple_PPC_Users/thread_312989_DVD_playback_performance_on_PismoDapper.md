---
title: "DVD playback performance on Pismo/Dapper"
date: 2006-12-05
forum: Apple PPC Users
---

### Post by dpny on 2006-12-05
I finally got around to getting DVD playback working on my Pismo under Dapper. However, performance seems to be less than great: reading off the disc the picture will stutter every few seconds and CPU usage is about 85% when playing in a window. Does anyone else have experience with DVD playback on a similar machine (500 MHz G3)? Is this normal, or are their some optimizations of which I'm not aware?

---

### Post by galvatron1983 on 2006-12-05
It could simply be the age and configuration of your mac that causing the problems. As far as I recall the predecessor to your model was the 400Mhz G3 PowerBook and that required an extra DVD video decoder card in order to play DVDs. The cpu and hardware itself wasnt powerful enough to decode the MPEG 2 video found on DVDs on its own. Your model was the first Powerbook that had enough computing power to be able to playback DVDs without additional hardware. My theory is a DVD would probably playback fine in OS 9 which is an older and less resource hungry OS compared to the latest version of Ubuntu. My knowledge of old macs is pretty comprehensive but Im not a Linux expert so I could be wrong here.

---

### Post by dpny on 2006-12-05
I thought it might be something along those lines. I wonder if it could also be that the open source driver for my video card (r128) doesn't have as many bells and whistles as the ATi drivers Apple uses in OS X.

---

### Post by galvatron1983 on 2006-12-05
Compatability with hardware on the powerpc version of Ubuntu isnt great, particularly for things like graphics cards. Maybe you could try searching the forums for your make of graphics card, perhasp there is a powerpc driver for it

---

### Post by dpny on 2006-12-05
> **galvatron1983 said:**
> Compatability with hardware on the powerpc version of Ubuntu isnt great, particularly for things like graphics cards. Maybe you could try searching the forums for your make of graphics card, perhasp there is a powerpc driver for it

Well, there is the r128 driver I am using, but I will search for more.

---

### Post by didg on 2006-12-05
There's an option, cf. man r128

       Option "DMAForXv" "boolean"
              Try or don’t try to use DMA for Xv image transfers. This will reduce CPU usage when playing big videos like
              DVDs, but may cause instabilities.  Default: off.


Did you try it?

---

### Post by dpny on 2006-12-05
> **didg said:**
> There's an option, cf. man r128

       Option "DMAForXv" "boolean"
              Try or don’t try to use DMA for Xv image transfers. This will reduce CPU usage when playing big videos like
              DVDs, but may cause instabilities.  Default: off.


Did you try it?

Nope, but I will give it a shot tonight.

---

### Post by dpny on 2006-12-07
> **didg said:**
> There's an option, cf. man r128

       Option "DMAForXv" "boolean"
              Try or don’t try to use DMA for Xv image transfers. This will reduce CPU usage when playing big videos like
              DVDs, but may cause instabilities.  Default: off.


Did you try it?

Tried it. No such luck.

---

