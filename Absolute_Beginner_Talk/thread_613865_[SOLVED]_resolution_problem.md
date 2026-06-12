---
title: "[SOLVED] resolution problem"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by White-Wolf52 on 2007-11-15
hi, im using a nvidia 6800 video card with 2 monitors(samsung syncmaster 226bw, and a dell e173fp) on Ubuntu 7.10. i have two problems
1) when i try to switch the syncmaster to being the default moniter, it just acts as if the e173fp is: 

currently i have the e173fp as the default and the syncmaster as the secondary, like this the syncmaster is working fine, but the dell is not(the second problem)

2)the dell moniters edges are not set at the edge of the moniter, the screen ends at the edges, but it scrolls farther on that moniter as i keep moving the mouse.

---

### Post by Inxsible on 2007-11-15
open up a terminal and type in```
gksudo nvidia-settings
```Make your Syncmaster as the primary monitor and select the resolution you want.

Then select Twinview option and make your Dell as your secondary monitor and also select the appropriate resolution for it.

In the end DO NOT FORGET to click "Save to configuration file" button

---

### Post by White-Wolf52 on 2007-11-15
well, thx again for ur help, worked again :D

---

