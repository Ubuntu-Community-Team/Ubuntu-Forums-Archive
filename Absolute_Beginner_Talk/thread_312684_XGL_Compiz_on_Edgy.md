---
title: "XGL Compiz on Edgy"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-12-04
I must use XGL as my video card doesn't get a good refresh rate with the 
latest nvidia driver (despite many workarounds) and that's what's needed for 
AIGLX. I'm wondering if there is a way to get Compiz running with XGL on 
Edgy? I've tried using AIGLX's guide for compiz, altering it to meet XGL's 
setup standards, but I haven't really gotten anywhere. Does anyone know of a 
way to make this setup possible? I'd really appreciate it!!

---

### Post by shanepardue on 2006-12-04
I have gotten the gandalf repo set up and I installed the necessary Compiz 
packages, but I'm not getting any windows borders or effects. I've made sure 
the color depth is at 24 and I'm still experiencing problems. Please help!

---

### Post by shanepardue on 2006-12-04
I figured out how to make AIGLX for me....

gconf-editor then go into apps->compiz->screen0 then untick detect refresh rate and set your own refresh rate.

---

