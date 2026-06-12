---
title: "No sound in gutsy on HPDV9575"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-10-18
Hi I recently installed the new version of 7.10 (downloaded the official iso).

Installed correctly -> No sound

Tried following the guide on: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

the device manager says it's a 82801H (ICH8 Family) HD Audio Controller


plz help me install the sound card!

---

### Post by aktiwers on 2007-10-18
What output does this command give you?
 ```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by Fixel on 2007-10-18
None. =(

---

### Post by Fixel on 2007-10-18
Reinstalled ubuntu and now it gave me:

Codec: Realtek ID 268
Codec: Motorola Si3054

what to do?

---

### Post by Fixel on 2007-10-18
Just tried the comprehensive guide, didn't work. bump..

---

