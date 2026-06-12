---
title: "Ubuntu won't boot! (video card unsupported i believe)"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by jugo23 on 2007-01-08
Please Help:

I stick the ubuntu cd in my drive. Boot priority is fine. The boot screen comes up. I press enter and it starts to boot. After a few minutes, the screen goes blank, as if it is still running, but now showing. My video card is a Radeon x1600. I figured Ubuntu didn't support it, and I would have to install the additional ATI drivers after installed. So I tried to install it using my onboard video card. I came across the same problem.

I have tried multiple copies of ubuntu with no luck. Different versions, Different copies, and no luck. I have tried using the "safe-graphics" mode. All of these problems lead me to the same blank screen that doesn't let me to even install ubuntu. 

Is there a way to fix this or boot with ATI graphics supported?

Thanks

---

### Post by scrooge_74 on 2007-01-08
do you get bump into terminal mode?

if not press CTRL+ALT+F1

log in, and try sudo dpkg-reconfigure xserver-xorg

and try the video drivers there, worst case you can use the vesa driver

---

### Post by jugo23 on 2007-01-08
I'll try that ASAP.

---

