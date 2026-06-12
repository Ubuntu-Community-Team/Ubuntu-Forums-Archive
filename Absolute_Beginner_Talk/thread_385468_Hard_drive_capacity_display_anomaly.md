---
title: "Hard drive capacity display anomaly"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-15
When I input```
sudo iwconfig
``` it says my hdb1 hard drive is 296GB, when it should be 320GB. The applications > accessories > disk usage analyzer tells a similar story. Where's that 24 gigs?

---

### Post by hardyn on 2007-03-15
are you sure its 'iwconfig'

that tells me about my wireless card...


that is a numbers game played by the hard disk manuf.
the hard disk guys define 1GB as 1000000000bytes
everybody else defines 1GB as 1073741824byles

so... 320 * 1000/1073 = 298GB

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

it's the way things have allways been... your not missing anything.

---

### Post by Griffiss on 2007-03-16
ah right ok that clears things up, thanks.

oh and bout the command, i meant ```
sudo lshw
```

recently took me three days to sort out my wireless so the iwconfig entry in the command line recall module of my brain is doubtless over-stimulated;)

---

