---
title: "update help please"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by marcopolo1981 on 2007-12-05
Hi everyone.
I have a problem with updates. Everytime I use update via terminal, synaptic or add/remove programs, I have to insert the ubuntu install disc. I didn't have to do this the last time I installed ubuntu, so what have I done different and is there a way around it? It isn't really a MAJOR problem as I generally have all my discs to hand anyway, but it can be a bit of a pain having to take out the disc I'm using at the time just to update.
Thanks in advance
Mark

---

### Post by Hospadar on 2007-12-05
System->Administration->Software sources

uncheck "installable from CD"

---

### Post by marcopolo1981 on 2007-12-05
Thank you very much! I can't believe it was that simple - I was expecting to become sudo and reconfigure using the terminal!
Thanks again
Mark

---

### Post by g2g591 on 2007-12-05
you could (I find it easier) sudo nano /etc/apt/sources.lst and comment out the cd line (which is exactly what that gui did)

---

