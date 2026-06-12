---
title: "Sound converter"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Patrickvv on 2007-02-20
ok so ive installed sound converter from synaptic and the output of mp3 is unavailable.it's greyed out so i cant convert files to mp3..how do i enable this ?
is there something i didn't do or install so that the mp3 output is available.

help greatly appreciated

---

### Post by RomeReactor on 2007-02-20
Hi. Perhaps you're missing some Gstreamer plugins. Look for **gstreamer0.10-plugins-ugly** and **gstreamer0.10-plugins-ugly-multiverse** in Synaptic; if they don't appear, you need to enable the Universe and Multiverse repositories. To do that, on Synaptic go to "Settings-->Repositories" and on the first tab (should say "Ubuntu 6.10" if you're on Edgy) check all the boxes there; now press the Reload button and search again.

---

### Post by vitalstatistix on 2007-02-20
Hey try this link, though its for sound juicer it shd work:
[https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58](https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58)

---

### Post by Patrickvv on 2007-02-21
hey RomeReactor i allready applied universe and multi-universe from synaptic ever since i installed ubuntu.i also installed some gstreamer plugins.hold on i will check and post back

---

### Post by Patrickvv on 2007-02-21
its allright now. .mp3 is now available thanks

---

