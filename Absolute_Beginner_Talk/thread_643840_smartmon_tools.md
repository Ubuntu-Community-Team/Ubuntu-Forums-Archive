---
title: "smartmon tools"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-18
Hey guys quick question here I just bought a new external hard drive (Western Digital My Book 500g)

Anyways for some reason in linux it won't let me run the smartmontools.. Says not available or something.. But I can run them in windows with the provided software on the disk..

Anyways I had it for maybe 2-3 weeks now and already if I get a smartmon report it says for 

Relocated Sectors Value = 140 worth =200 thresh = 200 

Says its ok, but does this mean that its soon to be dieing or is the 140 value ok?

---

### Post by nick_h on 2007-12-18
Install smartmontools using:
```
sudo apt-get install smartmontools
```
Then run it using:
```
sudo smartctl --device=ata --attributes /dev/sda
```
(assuming an ata device on sda).
Look for the RAW_VALUE field rather than the VALUE field.  If it is 140 it is cause for concern.

---

