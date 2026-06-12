---
title: "having probs unloading sound model?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by blop on 2007-05-25
Hi all, having major issues with my sound card....hda intel thingy..

and i have been told to unload the sound module and reload it wilth a differnt option.

but when i run 

```
sudo rmmod snd-hda-intel
```

it tells me it is in use so i cant run it.....as far i can tell nothing is trying to use it....i have even rebooted 

cheers

---

### Post by johnny4north on 2007-05-25
link- [http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)
are you trying to do as the above link?  i think you can change the sound here:  panel > system > preferences > sound.  try setting the sound to alsa or oss on all settings, then reboot.  try to replace the module as the link suggests.  good luck..

---

