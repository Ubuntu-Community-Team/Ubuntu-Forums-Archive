---
title: "Disable optical sound on my macbook"
date: 2008-08-23
forum: Apple Hardware Users
---

### Post by ems5311 on 2008-08-23
Hey,
I boot into Ubuntu, and optical sound seems to be enabled all the time on my Macbook (Santa Rosa).  In OSX optical output is NOT always on.  I know it's costing me battery life when I'm disconnected, anyone have any idea how to disable optical output in Ubuntu?

---

### Post by cyberdork33 on 2008-08-24
run 'alsamixer' in a terminal. There should be a switch that you can turn off. (I think it is called IEC958 or so)

---

### Post by _mario_ on 2008-08-24
To disable optical sound on boot-up, add:
```
amixer set IEC958 off
```
to your /etc/rc.local. (Assuming it is IEC958 on your machine.)

---

### Post by sayad on 2008-08-24
i dont want to be disturbing but  i have never heard of optical sound , atleast bever in ubuntu , is it a new feature , but first of all is it any featuree of any help ?

---

### Post by ems5311 on 2008-08-24
> **sayad said:**
> i dont want to be disturbing but  i have never heard of optical sound , atleast bever in ubuntu , is it a new feature , but first of all is it any featuree of any help ?

Optical sound is a type of output that uses a laser to give your speakers the information on what sounds to make.  It is only used by specific types of wires (your regular headphones will not require optical sound).

Thanks a lot for that tip _mario_, it worked perfectly.

---

### Post by teklife on 2011-02-18
thanks for the terminal command mario, it turned off the optical audio lazer that was always on, however, now i cannot get any sound/signal through the headphone jack at all. i tried amixer set IEC958 on and the lazer is back on now, but still no sound output thru the jack. any tips?

*Update- i was able to get headphone sound by playing with the settings on "gnome alsa mixer"

---

