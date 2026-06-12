---
title: "Quake III Arena."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-09
Hi all,

I have a old version of Quake III installed on the Windows part of my computer, when I try to start it - an error message appears stating:

: could not find default.cfg

I have tried to rename my old cfg file to default but the same message came up?

Best Regards
Anders

---

### Post by The Titan on 2008-03-09
that is an issue with the PAK0.PK3 file.  Are you trying to run this in wine? There is a version for linux

---

### Post by lover_of_sc on 2008-03-09
Oh well I have tried both to start it with or without WINE. I have read that there is a version for linux out there but I am as far from a hacker as anyone could be. :-) Tried to figure out how to get the linux version and how to get it installed but no success so far... hehe

---

### Post by The Titan on 2008-03-09
> **lover_of_sc said:**
> Oh well I have tried both to start it with or without WINE. I have read that there is a version for linux out there but I am as far from a hacker as anyone could be. :-) Tried to figure out how to get the linux version and how to get it installed but no success so far... hehe
Its in the repos actually, just do 
```

sudo apt-get install quake3-data

```
then mount the cd (yes you need the cd, really stupid huh) and copy PAK0.pk3 to the baseq3 directory.  Or you could copy the one from your windows version, but it sounds like that one is corrupted.  should be a huge file, like 300mb or something(total estimate)

---

### Post by lover_of_sc on 2008-03-10
Thanks, now I just need to find my cd, have some sort of no-cd crack on my windows version - so I have no idea where it is.... Cheers for your help.

---

