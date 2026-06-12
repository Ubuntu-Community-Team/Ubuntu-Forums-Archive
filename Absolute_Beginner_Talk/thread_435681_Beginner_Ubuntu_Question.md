---
title: "Beginner Ubuntu Question ???"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by DrtBikDave on 2007-05-07
Is there anything simular to system restore in Ubuntu?

---

### Post by AAM on 2007-05-07
Dear DrtBikDave,

give us a bit of a chance and answer some question! 
1. What has happened? 
2. How long have you been on Ubuntu?

---

### Post by Outrunner on 2007-05-07
No there isn't.

---

### Post by Pobega on 2007-05-07
If you have an external drive, you can backup your Ubuntu installation to the drive. Or you can give Ubuntu 50% of your hard drive, and use the other half for backups.

Other than that, not really.

---

### Post by DrtBikDave on 2007-05-07
Answer:
 
 1.) After installing "DeVeDe" my computer will bog down and take very long to load internet pages. I was never able to make it work so I installed "K3b"
 2.) I have had Ubuntu installed for 1-1/2 Months but have only been installing stuff since last Thursday. 
 I am just curious if once I do something is there no turning back?

---

### Post by AAM on 2007-05-07
oh, that's a little easier! Yes there are roll-back mechanisms.

As a new user, I would recommend that you install everything according to the provided tools with APT or APTITUDE. This will mean that you will always be able to remove programs from within Synaptic or from the command line very easily. Give yourself another 4-6 months before trying compiling, although you can roll-back these changes also.

There is much less System Restoring to do because there are fewer System Stuff-Ups! I suggest that you keep a log of what you install and how you did it, which means that whenever it is all getting too messy, you can re-install the system and do a clean build back to your previous level - then set off messing it up again! Keeps me occupied for hours! To do this with some impunity, keep to one distro and have your home directory on a different partition to the root (/) directory.

I think the command to remove DeVeDe will look something like
> sudo apt-get remove DeVeDe
but you should look around at the apt HOWTOs to satisfy yourself that this is correct. Just as a byr-the-bye, have you looked for entries on DeVeDe to see if there is a fix for the aberrant behaviour. K3b is the best burning program available on Linux.

---

### Post by DrtBikDave on 2007-05-07
Thanks you were very helpful.

---

