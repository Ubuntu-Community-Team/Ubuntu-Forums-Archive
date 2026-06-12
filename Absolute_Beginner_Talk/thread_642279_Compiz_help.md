---
title: "Compiz help"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by littledude565 on 2007-12-16
Hey all i wondering how to use this ? like how can i install it?

---

### Post by awthomp on 2007-12-16
```
sudo apt-get install compizconfig-settings-manager
```

Then go: System -> Preferences -> Advanced Desktop Settings

Make sure your restricted graphics card driver is installed and "Custom" is selected under Visual Effects of System -> Preferences -> Appearance

---

### Post by Ub1476 on 2007-12-16
First of all, you need to turn it on in System>Preferences>Appearance>Visual Effects.

---

### Post by forestpixie on 2007-12-16
it is installed by default - you need thought o make sure you've got restricted drivers installed I think

to start use system > preferences> appearances - go to the visual effects tab 

to configure you need the settings manager

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by littledude565 on 2007-12-16
i keep getting this
"The composite extension is not available"

---

### Post by awthomp on 2007-12-16
try:

```
sudo apt-get install xserver-xgl
```

---

