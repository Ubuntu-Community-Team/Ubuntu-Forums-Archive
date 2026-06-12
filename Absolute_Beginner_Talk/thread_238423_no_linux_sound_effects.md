---
title: "no linux sound effects"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by feest on 2006-08-17
i don't know if this is just the point of the latest linux but when i worked with the previous ones and i opened a directory a sound was playing, thats gone? is that linux or my pc, also at certain programs there is no sound output...

---

### Post by it.henrik on 2006-08-17
Its been a very long time since I installed a fresh ubuntu.. but I cant remember hearing some sounds while opening folders. There is a sound playing when you click the "up" button in nautilus (the File Browser). If you can hear that sound I think its supposed to be this way :)

---

### Post by David Corrales on 2006-08-17
For dapper they disabled some sounds, which you can reenable at System -> Preferences -> Sound.
Some programs have problem playing sounds because Gnome is still using the ESD sound daemon which blocks the audio device (/dev/sound) and if other software tries to use it directly or via alsa they get problems. Eventually a new server like [http://pulseaudio.org/](http://pulseaudio.org/) will be integrated and make a lot of sound problems a thing of the past (hopefully).
In the meanwhile, some programs have the option to specify an external command to play a file. You can use **esdplay** to achieve this. Be sure to install the package esound-clients first though :)

---

