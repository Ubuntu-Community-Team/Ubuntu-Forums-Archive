---
title: "Sound..."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Toxic-Waste on 2007-04-20
My Sound Volume is too low!!! Anybody knows why this is happening? I can't listen to my music without being in a total silent environment. :confused:

---

### Post by RomeReactor on 2007-04-20
Hi. Enter **alsamixer** in a terminal to manage the volume levels of your soundcard's channels; "up/down" arrows to raise or lower volume, "left/right" arrows to move between channels, "m" to toggle mute or unmute, and ESC twice to exit alsamixer. There are graphical interfaces for alsamixer if you want:

```
sudo apt-get install alsamixergui
```

or

```
sudo apt-get install gnome-alsamixer
```

---

### Post by Toxic-Waste on 2007-04-21
Ok... I did all the above but the only thing I saw was that everything is at 100%. Something is not working properly obviously. Damn... :(

---

### Post by richtea on 2007-04-21
I get his problem too using Feisty live CD on my Gigabyte DS3P system with onboard sound.

Haven't installed on that computer yet so don't know if that would fix it. Maybe this is a know bug?

---

