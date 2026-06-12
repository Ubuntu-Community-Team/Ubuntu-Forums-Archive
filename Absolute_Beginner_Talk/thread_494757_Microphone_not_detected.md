---
title: "Microphone not detected"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by parry_mathur on 2007-07-07
I am using Ubuntu Feisty Fawn. I have installed audacity. When I try to record, it doesn't detect any signals from my microphone. Its working fine in windows. Also, the text in audacity is fuzzy and the menu bar is not displayed properly. Is there any fix to the **Microphone** problem?
Thanks

---

### Post by black_ice on 2007-07-07
i have the same problem ... 

however it was working fine on edgy without any problems !!!

if some one knows solution we will be thankful for him

---

### Post by forrestcupp on 2007-07-07
Try this.

In a terminal, type
```
alsamixer
```
It will bring up the command line version of alsamixer.

Push F4 to switch to the "Capture" settings.  Push the right and left keys to find the "mic" selection.  When you find it, press the up key to turn the volume up.  It should hear your mic after doing this.  It's just like in Windows how you have to make sure the recording levels are turned high enough.

You can do the same thing with the GUI mixer.  Right click on the volume icon in the taskbar and choose to show the mixer.

The reason the mic selection doesn't work in Audacity like it does in Windows is because in Linux, it is possible to record from multiple sources.

As for the blurry text, is it any different than the text in other programs?  Maybe you could try to install the Microsoft true type core fonts.
```
sudo aptitude install msttcorefonts
```

---

