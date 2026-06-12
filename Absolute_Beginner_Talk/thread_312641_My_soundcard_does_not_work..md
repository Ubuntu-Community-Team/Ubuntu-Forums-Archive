---
title: "My soundcard does not work."
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by cfsporn on 2006-12-04
When I first installed Ubuntu 6.06 LTS, my sound card was fine. However, a few weeks later it just stopped working. It shows up under the hardware manager, but it does not show up as an available output under the sound pref pane. An upgrade to Edgy did not help so what will. My soundcard is a SoundBlaster SB Live! EMU10k1 or a  CT4780 SBLive! Value

---

### Post by rsambuca on 2006-12-04
try running "alsaconf" in a terminal

---

### Post by cfsporn on 2006-12-04
Command not found.

---

### Post by rsambuca on 2006-12-05
hmmm...  how about this

```
sudo /etc/init.d/alsa-utils reset
```

---

