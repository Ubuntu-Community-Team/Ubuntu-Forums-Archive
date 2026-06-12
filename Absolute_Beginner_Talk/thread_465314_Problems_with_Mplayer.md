---
title: "Problems with Mplayer"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-06-05
ok, I have a problem with MPlayer.

When I try and open a Video with MPlayer (.avi, .wmv) I get this message:

```
Error opening/initializing the selected video_out (-vo) device 
```

I have tried removing MPlayer via synaptic and all the related packages I could find (I may have missed some) and reinstalling them, but still no luck.

any ideas?

---

### Post by taurus on 2007-06-05
Open MPlayer by itself and go into Preferences -> Video and pick **xv** as a driver.  Close down MPlayer and open it again.  It should play your videos now.

---

### Post by zvacet on 2007-06-05
Preferences>video>x11

---

### Post by Jamesbowden on 2007-06-05
Setting Video playback to x11 worked, tyvm

---

