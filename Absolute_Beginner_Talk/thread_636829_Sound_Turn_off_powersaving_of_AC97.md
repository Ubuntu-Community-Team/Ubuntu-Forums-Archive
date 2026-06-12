---
title: "Sound: Turn off powersaving of AC97 ?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Scarath on 2007-12-10
I have been having problems with my sound, trying for weeks to get it working, tried everything on the forums etc etc (boohoo i'm over it)

But then I saw this bug report and at the bottom there is an interesting account of how someones sound worked in gentoo and not ubuntu.
Anyway i wondered if that might be the problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174199](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174199)

It says that in Gentoo the 'power saving of AC97' is turned off, does anyone know how i can check this and whether there is a terminal command to turn power saving of the sound card off?

I hope they get the sound problems sorted by 8.04, i think sound is one of the biggest problems on these forums next to ATI.

Thanks

---

### Post by hopelessone on 2007-12-10
Tips & Tricks

AC97 audio power saving mode

[http://www.lesswatts.org/tips/misc.php](http://www.lesswatts.org/tips/misc.php)

:)

---

### Post by Scarath on 2007-12-10
thanks for the link, turns out my powersaving was Off anyway as the command
> 
cat /sys/module/snd_ac97_codec/parameters/power_save

returned 
> 
N

Bah, never mind, still no sound till 8.04 (fingers crossed)

---

