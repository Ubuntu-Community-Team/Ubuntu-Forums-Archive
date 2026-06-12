---
title: "correct monitor settings to center desktop (dual boot)"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by jodansmif on 2007-09-07
I am currently running XP and recently put in a Ubuntu partition for school work. The install went great but the desktop is off center compared with my XP installation. I could of course change my monitor's settings with the controls on the front but to be honest, I use XP much more currently and I was hoping there was a way I could fix this inside Ubuntu (or XP for that matter) which would make it unnecessary to manually adjust my monitor controls every time I switch OSes. Though I am dreading hearing the phrase "xorg.conf"... I'll take what I can get. 

Thanks!

---

### Post by fazillatheef on 2007-09-07
maybe because your graphics card driver is not installed properly

---

### Post by dickohead on 2007-09-07
I had the same issue when I was using an Onboard Nvidia graphics card. I updated the NVidia display drivers and edited the (here it comes) xorg.conf file to load the nvidia drivers instead of the nv ones.

There are plenty of posts around that will tell you how to update your drivers.

Good luck.

---

### Post by jodansmif on 2007-09-07
Oh... I just assumed when the system updates ran on first boot that I got the most recent drivers. Learn something new everyday, I guess. So the idea is that once I get the new drivers installed that will fix the problem or that will enable me to change some settings manually to fix the problem?

---

