---
title: "DVD-ROM Problem.."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Stikky on 2007-11-16
Hey everyone,

I am having a few problems with my DVD-ROM drive.. It's in my laptop and it's a DVD-ROM/CD-RW combo drive (yeah, it's an old laptop) and I have a DVD that has a few videos and pics on it of my family in the states and it won't work! Every time I try and use the disk, it says that there's no media in the drive..

I tried another DVD (outkast, I believe) and it worked fine, so it can read DVDs but for some reason, it won't read this one. I have tried it on a windows computer (my work comp) and it works fine but since gutsy didnt like my partitions on my laptop, I dont have a windows machine at home.. Anyone able to help me out here? Any ideas what might be going on?

Thanks in advance,
Stikky

---

### Post by severedspirit on 2007-11-16
hmm, are you sure the media is clean? Also due to the age of the DVD drive it may be slower than ones able to use error checking. Can you at least hear the DVD trying to load?

---

### Post by Stikky on 2007-11-16
The DVD spins up and everything, the light on it flashes and it sounds like it's thinking and then it stops.

I'm not sure what you mean by the media being "clean" but it was burnt by my uncle on his windows comuputer using nero.. I dunno if that info helps, if anyone wants to know more about where the DVD comes from, I can ask him but it has worked fine on all the windoes machines I have tried it on.. My work computer, my parents' desktop (both XP) and my mym's vista laptop so I dunno why ubuntu wont use it..

---

### Post by Stikky on 2007-11-20
Anyone have any idea what might be going on here??

Still can't get this DVD working...

---

### Post by Atomic Dog on 2007-11-20
on all my laptops I had to change the fstab entry for my dvd drive.  Your disc may be in UDF format and the way the fstab entry is written, for some reason, would not let my drives mount them.  I changed the entery to:

/dev/scd0 /media/cdrom0 auto user,noauto 0 0

from the original:

/dev/scd0       /media/cdrom0   iso9660,udf user,noauto     0       0

Now you might want to do a forum search on the UDF issue to shed light, but it's worth a shot changing it and see what happens.  Your drive may not be scd0 so make sure you just change the text after /media/cdromx

Also make sure you backup fstab first!  And you will have to reboot for the change to take effect.

Hope this helps.  if it does please report back/

---

