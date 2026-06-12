---
title: "recording desktop"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-07-10
what is the package called i need to install that enables me to do this

---

### Post by Adramelech on 2007-07-10
recordmydesktop
gtk-recordmydesktop

---

### Post by k33bz on 2007-07-10
ok, i got that working, is there a way to convert the vid files from .ogg to .wmv

---

### Post by Golyadkin on 2007-07-10
I am not sure if you can, isn't .wmv a proprietary codec by Microsoft?

---

### Post by Mrhankymk on 2007-07-10
Yes, it is. A bad format in the first place though. Just like BMP from Microsoft the file sizes are outrageously huge. I'm sure there's a way to convert over to AVI, FLV, etc.

---

### Post by AlexenderReez on 2007-07-10
if you have beryl installed with mencoder......and you have video recording plugin,this will enable you to record and convert automatically to avi and write time and date for you record....


> seom-filter /home/<username>/<folder video capture>/beryl-capture.seom | mencoder - -ovc xvid -xvidencopts bitrate=1200 -o /home/<directory>/folder video capture>/capture-`date +%d-%m-%y_%H%M`.avi

---

