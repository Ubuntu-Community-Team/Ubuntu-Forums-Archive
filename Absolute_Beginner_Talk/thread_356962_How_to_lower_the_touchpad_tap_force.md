---
title: "How to lower the touchpad tap force?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-02-09
Hi,

I've tuned my touchpad the way I want but I cannot achieve to lower the amount of force required for a tap to be registred. Is there any command to do that in xorg.conf as an option of the synpatic device???? I find that the touchpad tap is less sensitive than in XP....

Thanks

EDIT:Solved: I had to set a lower value for FingerHigh (and FingerLow) in xorg.conf, following [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by dbbolton on 2007-02-09
you can mark your thread as solved via- edit > go advanced

also, thanks for sharing your answer.

---

### Post by kilou on 2007-02-10
However you shouldn't set the FingerLow value too low otherwise you'll get movements when releasing the finger from the touchpad. In fact it seems quite good to have FingerHigh>FingerLow sometime. My cirrent settings are:
FingerHigh=18
FingerLow=20

---

