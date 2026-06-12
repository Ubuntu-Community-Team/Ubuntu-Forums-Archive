---
title: "[SOLVED] Networking Reset"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Phoenixzeus on 2008-03-24
Hi,
At the moment my wireless connections (I have two different cards with two different chipsets and drivers) both hang randomly. Usually happens when I am fiddling with connecting to different networks and detecting hotspots, from what I can gather this is known to happen on a few cards or chipsets. I was wondering if anyone knows a command to reset the network connections (Similar to ifconfig x down/up)
Something like the ctrl +alt + Backspace, but for networking. Does anyone know if there is even indeed such a command?
Many thanks
Mitch

---

### Post by kpkeerthi on 2008-03-24
```
sudo /etc/init.d/networking restart
```

You may also use **stop** and **start** in place of **restart**

---

### Post by Phoenixzeus on 2008-03-24
Thank you for your quick responce kpkeerthi.

---

