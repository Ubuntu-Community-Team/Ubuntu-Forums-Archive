---
title: "lcd resolution &gt; 1024 with r128 m3"
date: 2004-12-13
forum: Apple PPC Users
---

### Post by robsta on 2004-12-13
Hello, 

is there any possibility to run a resolution > 1024x768 on the lcd out of a r128 M3 equipped late 2001 iBook?
Using m3mirror from [http://penguinppc.org/~benh/](http://penguinppc.org/~benh/) and a patch from [http://stampflee.com/kernel/index.shtml](http://stampflee.com/kernel/index.shtml) i can use an external VDU, but only up to 1024x768.

Thanks, 
Rob

---

### Post by cow_racer on 2004-12-13
I have gotten mine to get 1600x1200 when I was trying to play with configuring the XF86Config-4.   In the monitor section I set the HorizonRefresh to 75.  When I start x, it gives me 1600x1200 at 60 Hz.  You should disable your lcd before you start X.

---

### Post by robsta on 2004-12-13
Heh cool!
Could you send me you XF86Config-4 or post it here? (robsta AT stereolyzer DOT net)
Thanks, 
Rob

---

