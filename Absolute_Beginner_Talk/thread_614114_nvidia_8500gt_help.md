---
title: "nvidia 8500gt help"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2007-11-15
Ok, i ran the live cd Ubuntu 7.10 64bit and everything looked great, After I installed I can't get the resolution above 640x480 Please help, I should be able to run 1440x900, and it worked on the live CD.  I have enabled the restricted drivers, and it shows up in the device manager , but device type and capabilities show up as unknown. I have never had to configure this before so any help would be great. and remember I'm a newbie.

---

### Post by overdrank on 2007-11-15
HI and I would recommend Envy
 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Partyboi2 on 2007-11-15
You could try adjusting it in Nvidia Settings
```
nvidia-settings
```Then click on:
 X server display configuration, and change the resolution to what you would like it to be.
:)

---

### Post by nikolas68 on 2007-11-15
To install support for Nvidia cards, follow these steps:
1. Select System &#10148; Administration &#10148; Synaptic Package Manager.
2. Click the Search button and enter nvidia-glx as a search term. In the list of results, click
   the check box next to nvidia-glx and also nvidia-settings, so that both are marked for
   installation. Then click Apply.

---

### Post by Hospadar on 2007-11-15
you'll need nvidia-glx-new, not nvidia-glx

---

### Post by henky on 2008-01-18
tried this, but didn't work, i installed nvidia-glx-new but on bootup my screen went black and the monitor told me the resolution was too high:S

---

