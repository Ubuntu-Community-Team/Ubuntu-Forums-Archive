---
title: "Possible to switch USB audio device without root perms?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-08-13
I have a laptop with an internal soundcard but also have a USB soundcard.

Currently im using the following command (well i've got it as a script, to point and click at)
```

sudo asoundconf set-default-card Audio

```
where Audio is the name of my usb-soundcard.

Only problem with this is I'm required to enter my password everytime, and people who dont know my password and using my pc can't do it.

So i ask, is it possible to switch to usb audio without sudo perms.

Thanks

---

### Post by bodhi.zazen on 2007-08-13
run the command without sudo

See this link as well :

[https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea](https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea)

---

### Post by PetePete on 2007-08-13
thanks, but running without sudo doesn't do anything (command runs ok, but no change in audio)

added those things to bottom of  /etc/modprobe.d/alsa-base but how do i now change between the cards?

---

### Post by bodhi.zazen on 2007-08-13
reboot & check it out.

See also sound/mixer, the little speaker icon in your tray, that should let you change sound cards as well.

---

### Post by PetePete on 2007-08-13
much appreciated help, but ive restarted and still see no option to switch cards.

Im using KDE btw, and Kmix, should i install a different mixer?

---

### Post by bodhi.zazen on 2007-08-13
oic

See if this link helps : [http://andrew.org/index.php/archives/2006/11/29/kde-select-audio-device/](http://andrew.org/index.php/archives/2006/11/29/kde-select-audio-device/)

---

