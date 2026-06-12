---
title: "Ubuntu boot sequence"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-05-18
When I turn on my pc and ubuntu starts up everything works quickly until it gets to "configuring network devices" or something like that.  Is there any way I can bypass that part of the bootup, because the computer stops for at least a minute trying to pick up a network device.

---

### Post by bluevoodoo1 on 2006-05-18
ctrl+c

should get you past it!

---

### Post by xXx 0wn3d xXx on 2006-05-18
You can press CTRL + C to continue on. You can also edit you interfaces file to stop it from stalling. type this in terminal:

> sudo gedit /etc/network/interfaces

Now, open up System > Administration > Networking. There should be a few interfaces (wlan0, eth0, ppp) and see which one you are using. Let's say you were using eth0, leave that in your interfaces file but remove any others that you don't need. Then just save and close.

---

### Post by Moebius on 2006-05-18
You can always hit ```
 Ctrl + C 
``` to skip that part (or any other item in the boot process).

---

### Post by abbrew on 2006-05-18
Thank you very much for the help!

---

