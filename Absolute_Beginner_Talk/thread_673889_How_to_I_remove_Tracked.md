---
title: "How to I remove Tracked ?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by MaximB on 2008-01-21
Tracked starts every time I login and it's taking many resources.
What it's supposed to do ?
If it's not critical, how can I remove it ?

---

### Post by banewman on 2008-01-21
Just searched synaptic and can't find tracked - did you install it?
Try in a terminal -
sudo updatedb && locate tracked
and if it is found browse to the folder it is in and do some reading.
Hope it helps and let us know how it goes pls. :)

---

### Post by bollix47 on 2008-01-21
I think the OP means tracker.

System > Preferences > Sessions

Remove the tick mark next to tracker.

---

### Post by MaximB on 2008-01-22
Just removed that useless consuming memory program.

sudo apt-get purge tracker

---

