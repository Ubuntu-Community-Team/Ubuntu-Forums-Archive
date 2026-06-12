---
title: "Dell Inspiron E1505 3D Acceleration"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by cosmiccharles on 2007-10-25
I have recently installed Gusty Gibbon on my Dell E1505 laptop and I am not sure if I have the proper video drivers for 3D acceleration. Being a newbie, it is hard to fully understand exactly what the problem is but when trying to load 3D video games and other various 3D software I get a message that says I need specific drivers for 3D acceleration. Some 3D applications do run but they flicker a lot and I tend to see my desktop in between the flickering. This also happens when my screen saver comes up as well. It is somewhat hard to figure out exactly what video card I have since Dell pumps out 3 or 4 different laptops under this Inspiron model but i believe it is a Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller. Anyone know what I need to do to get this to run right? 

When I do: 

**glxinfo | grep rendering**

I get this: 

**direct rendering: No (LIBGL_ALWAYS_INDIRECT set)**

---

