---
title: "Monitor refreate rate so much less then before ?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by moehabibi on 2008-04-19
Hey ... 
i have a problem  

iv have eye strian for the last week 
and i think its cuz of my monitor 
when i see the refress rate ... i see 50 
when i had windows vista.. my reefresh rate was 60/72/75 

how come i dont have these options on ubuntu ... 
this eye strian is killing me :(

---

### Post by overdrank on 2008-04-19
> **moehabibi said:**
> Hey ... 
i have a problem  

iv have eye strian for the last week 
and i think its cuz of my monitor 
when i see the refress rate ... i see 50 
when i had windows vista.. my reefresh rate was 60/72/75 

how come i dont have these options on ubuntu ... 
this eye strian is killing me :(

HI and if you have the nvidia drivers installed then you may use the alt, F2 keys and use this command ```
gksudo nvidia-settings
``` to adjust your refresh rate and resolution.

---

### Post by syczu on 2008-04-19
Try
> sudo dpkg-reconfigure xserver-xorg

And step-by-step configure your video.

---

