---
title: "no desktop effects!! help!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by colomob on 2007-11-21
:(i have festy and everytime i enable desktop effects the screen goes white..what can i do. i check therestricted drivers and it says no drivers are restricted..i need help here

---

### Post by Haluci on 2007-11-21
most likely your video card doesn't support desktop effects.

---

### Post by colomob on 2007-11-21
this is the second time i install ubuntu on the same laptop and the first time it did work..

---

### Post by jordank on 2007-11-21
do some video cards just not support effects like desktop cube?

---

### Post by jordanmthomas on 2007-11-21
> **colomob said:**
> :(i have festy and everytime i enable desktop effects the screen goes white..what can i do. i check therestricted drivers and it says no drivers are restricted..i need help here

What kind of graphics card do you have?

[quote=jordank]do some video cards just not support effects like desktop cube?[/quote]
This is true (in a simplified answer).  My desktop at home has an old ATI RAGE 128 and the drivers it uses don't provide the features compiz needs.

---

### Post by MrFSL on 2007-11-21
Identify your graphics hardware:
```
lspci | grep -i vga
```

---

### Post by colomob on 2007-12-03
i have a nVidia Corporation C51 PCI Express Bridge (rev a2)

---

### Post by LowSky on 2007-12-03
um that is one odd sounding video card...

chances are yu need a different driver and you should upgrade to gutsy

---

