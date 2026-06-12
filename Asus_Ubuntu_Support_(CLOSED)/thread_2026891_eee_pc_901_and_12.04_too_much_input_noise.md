---
title: "eee pc 901 and 12.04: too much input noise"
date: 2012-07-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by anoe on 2012-07-15
hi all, i have been running ubuntu in my notebook (eee pc 901) for three years now, i begun with lucid but settled up with natty, optimized for audio performance. I made un upgrade to precise some weeks ago and now there is too much noise in the sound input, it's not  question of the input volume 'cause it's low, and if i get it lower then you just can't  listen to the real input.

I didn't change anything myself to the configuration files, in /etc/modprobe.d/alsa-base.conf I still have the line options snd-hda-intel model=eeepc-p901. It happens not only with alsa, but also when running jack.

Any suggestion?

tx

---

### Post by OldAdamUser2 on 2012-08-29
I have a feeling that you know more about this than I do, but I solved a similar problem by using alsamixer. I raised the "Capture and "Capture 1" settings, as well as the two mic boost settings, adjusting the various values until I liked the way things worked. I needed to do this to get Skype working correctly.

---

### Post by anoe on 2012-10-12
hi there,

tx for your answer. I tried and it's working better. In my case, no mic boost and all the way with the mic in.

xxx

---

