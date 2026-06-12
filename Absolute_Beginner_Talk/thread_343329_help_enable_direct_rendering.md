---
title: "help enable direct rendering"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-01-21
my graphic card is Intel Corporation 82852/855GM, driver i810. i want to enable direct rendering in order to make beryl work
> 
glxinfo | grep direct
direct rendering: No


> 
lsmod|grep 915
i915                   21632  2
drm                    74644  3 i915
tsdev                   9152  0



---

### Post by CroEragon on 2007-01-21
First make sure that you have 3D rendering on your card. AFter that i enabled it with using official drivers, not open source ones. You'll have to found guide for your specific card.

---

