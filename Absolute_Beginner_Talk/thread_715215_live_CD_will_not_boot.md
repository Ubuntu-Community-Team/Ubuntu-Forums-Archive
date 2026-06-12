---
title: "live CD will not boot"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-03-04
ok so i have had ubuntu on my laptop for a while now but now i want to do a dualboot. and it is really hard to do a dualboot with the alt CD i have used the alt CD on all of my installs. but when i but the live CD in and boot from it and try to start ubuntu it will start to go but the screen goes black after the bar goes around like a million times but i can boot from it some time about 2 out of 5 times and when i do boot it is really slow and stops working a lot when trying to install. would getting more RAM be a help to do this. i have 256mb now with a 9xx MHz PIII if i upgrade to 384MB will it help. also if any one has somthing to say about the screen going black it normaly goes to a _ (flashing) then a black screen after it does all of its {OK} and stuff like that.


David

---

### Post by Gepetto on 2008-03-04
Adding more ram won't hurt. It also could be that the computer simply can't handle everything, in which case, you would have to use the alt cd for the install. I guess you could also try using safe graphics mode too while installing.

---

### Post by kellemes on 2008-03-04
I'd absolutely go for [xubuntu]("http://www.xubuntu.org/").

---

### Post by divindavid on 2008-03-04
i know i would have to use an alt cd for an install would adding more ram help the install. there is no such thing that a computer cant handle it (in our case) but i am just asking will adding ram help the live cd install and that is happening with the start up when i had ubuntu on this computer i would get the same black screen after the _.

---

### Post by divindavid on 2008-03-04
i hate xubuntu i love ubuntu i have been running ubuntu 7.10 on this for a while now but i just uninstalled and put XP on it for the time being to get the install working

---

### Post by Tatty on 2008-03-04
You should be able to partition fine with the alternative CD.  I installed a dual boot with it several times in the past.

---

### Post by divindavid on 2008-03-04
i have tryed several times but it is really difficult because when ever i try to partition the drive i get a error

---

### Post by divindavid on 2008-03-04
plus it is much harder to install a dual boot on a alt CD

---

### Post by divindavid on 2008-03-04
i am just asking would the live cd install work better with the upgrade of ram

---

### Post by kellemes on 2008-03-04
> **divindavid said:**
> i am just asking would the live cd install work better with the upgrade of ram

The black screen you talk about will not change by upgrading ram. You can either try another distro or try the the alternate installer so you can install the system without having to deal with livecd giving you crap.
If it is related to your videocard try to issue the following to see if you at least get X working.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

