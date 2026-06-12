---
title: "Lost Audio iMac Slot Loader"
date: 2010-07-08
forum: Apple Hardware Users
---

### Post by markosjal on 2010-07-08
MY new install of 10.04 was working great on the iMac G3 . I was so impressed, but then my sound stopped working. 

I hear  the "BONG" at start up but no sound in ubuntu.

Any Ideas?

---

### Post by linuxopjemac on 2010-07-08
You might want to add

```
dmasound-pmac
-r dmasound-pmac
snd-powermac
```

to /etc/modules

---

### Post by markosjal on 2010-07-08
did not work


adding what you suggested means it now looks like this:

snd_powermac
apm_emu
snd-powermac
dmasound-pmac
-r dmasound-pmac
snd-powermac

the last line now appears 3 times.

---

### Post by linuxopjemac on 2010-07-08
try to unmute channels with alsamixer ?

---

### Post by markosjal on 2010-07-20
I found out what is happening with this. 

Sometimes on reboot, there is no sound. 

If I plug in a headphone then unplug, the sound returns.

This leads me to believe that the autdetection of the headphones is somehow messed up.


Also, I can not install the Gnome Alsa Mixer. ports.ubuntu.com can not be respolved when trying to install.

---

