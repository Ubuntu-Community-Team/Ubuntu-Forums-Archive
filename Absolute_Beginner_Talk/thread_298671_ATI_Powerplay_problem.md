---
title: "ATI Powerplay problem"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by davebed on 2006-11-13
I somehow got my ATI x1400 to scale down to a lower power level when on battery and up to full power when on AC.

The problem is that if I start up on battery, the above even is not triggered. Only if I plug into AC and then unplug does the card power itself down to a lower state. When i start up on battery, i have to manually issue the command
```
DISPLAY=:0 /usr/bin/aticonfig --set-powerstate 1
```


Can anyone figure out how to have it automatically check if it's on battery on startup and scale itself down to the low power state?
Thanks

---

