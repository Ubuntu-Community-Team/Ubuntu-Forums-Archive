---
title: "Downloading and Adding software?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TheBlackWizard on 2007-07-03
I don't know how to install new software to Linux...

I am wanting to add a heat monitoring software, called lm_sensor, from 

[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

but I don't know how...

Any assistance would be greatly appreciated!

---

### Post by Nekiruhs on 2007-07-03
```
sudo apt-get install lm_sensors
```
Or just open up synaptic under administrations and search for it.

---

### Post by benanzo on 2007-07-03
The **lm-sensors** package is included in the Ubuntu repositories.  To install it go to **System -> Administration -> Synaptic Package Manager** and search for **lm-sensors**.  When it comes up right-click it and select **Mark for Installation**.  Then click **Apply**.  It wil download and install it automatically.

You could also use the terminal (**Applications -> Accessories -> Terminal**)
```
sudo apt-get install lm-sensors
```

Good Luck!

---

### Post by TheBlackWizard on 2007-07-03
Heheheh....

I am such a noob....

So, now that it is downloaded and installed....


How do I use it? :D

---

### Post by Raineer on 2007-07-03
Yeah it's just a library that enables the reading of the sensors.  Now you can get a widget to read them, there are many...

I use gkrellm (also installable via apt-get), but there are plenty more that are available depending on your desktop.

---

### Post by forestpixie on 2007-07-03
sensors

it might give you need to run sensors-detect

---

### Post by TheBlackWizard on 2007-07-03
Is there one that tells the temp of the CPU?

---

### Post by Raineer on 2007-07-03
CPU, GPU, All your HDD's, and any "zone" sensors the motherboard might have.

---

### Post by TheBlackWizard on 2007-07-03
Found it...

Right click Gkrellm window header, choose sensors, open the tab for temp, select the boxes.

Thank you for all your help!

---

