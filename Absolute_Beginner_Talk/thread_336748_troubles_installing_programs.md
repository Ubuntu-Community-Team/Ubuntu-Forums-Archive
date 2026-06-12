---
title: "troubles installing programs"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by noenter1 on 2007-01-12
Ok I am trying to install a few programs(wine, automatix, rar, ect..., and for every program I try to install I get this: ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
And it wont let me install anything that isnt thru the synaptic packet manager.

---

### Post by tonyr1988 on 2007-01-12
You can't use two "installation" programs at once. This includes:

-Automatix
-Synaptic
-Aptitude (from Terminal)
-Apt-Get (from Terminal)

Make sure you aren't running two of those at once.

---

### Post by noenter1 on 2007-01-12
Oh ok now I feel stupid I had syaptic open while trying to install programs in the terminal. Thanks for pointing that out :)

---

