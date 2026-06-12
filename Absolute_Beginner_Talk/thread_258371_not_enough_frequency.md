---
title: "not enough frequency"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-15
Buneos noches amigos ubuntos,

i've been trying to get my ATI X800 dual head to work properly for a whole week now (been working on it only a bit in the evenings ;)). I figured out everything so far, I have two screens up and running and the desktop spreads out nicely on two screens with xinerama. But both monitors are running with 1024x768@85Hz only and it's seriously bugging me because they are capable of so much more. They could do 1024x768@120Hz or some higher resolution with 100Hz. Anyways, now that I turned xinerama on, I can't change the resolution and frequency anymore. System -> Preferences -> Screen Resolution says "The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available.". Can anyone please give me a hint how to proceed from here? I don't see what I could set in xorg.conf to boot with a higher frequency. Here is a Monitor section from my xorg.conf with the HorizSync and VertRefresh params set to exactly the monitor's specifications.

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        HorizSync    30.0 - 96000.0
        VertRefresh  50.0 - 160.0
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS"
EndSection


Thanks,
Cruz

---

### Post by Cruz on 2006-09-16
Well to be exact I made a mistake there, because the Horizsync is provided in kHz. So my Monitor sections look like this now:

Section "Monitor"
Identifier "aticonfig-Monitor[1]"
HorizSync 30.0 - 96000.0
VertRefresh 50.0 - 160.0
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS"
EndSection


Not that it makes any difference.

Cruz

---

### Post by petri on 2006-09-16
For the first your **HorizSync 30.0 - 96000.0** should be **HorizSync 30.0 - *96.0*** 
for the second I don't know anything about xinerama.

My xorg.conf says

```
Section "Monitor"
	Identifier	"NEC FE950+"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection
```

---

