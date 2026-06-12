---
title: "Canviar bitrate AC3"
date: 2011-04-15
forum: Catalan Team
---

### Post by ibea on 2011-04-15
Hola a tothom. 
Sabeu si hi ha algun programa a Ubuntu que permeti canviar el bitrate de fitxers d'audio AC3 mantenint el número de canals intacte?
Ho he provat amb l'Audacity, però el temps que deia que tardaria a fer-ho era massa gran. 

Merci

---

### Post by wgarcia on 2011-04-15
Em sembla que ho pots fer amb "ffmpeg", una cosa així:

```
ffmpeg -i soundA.ac3 -acodec ac3 -ab 384 soundB.ac3
```

on "soA.ac3" és l'origen, "soB.ac3" és el destí, i 384 és el "bitrate" desitjat, però no estic segur, no l'he provat.

---

