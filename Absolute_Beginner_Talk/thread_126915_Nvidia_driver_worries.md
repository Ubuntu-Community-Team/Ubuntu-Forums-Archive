---
title: "Nvidia driver worries"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-02-07
Hi, ive just reinstalled my ubuntu on a newer machine
The old one had a geforce 2 and was real jerky on the graphics until i installed the latest nvidia driver from the nvidia site. 

The new PC has a geforce 4, I tried to repeat the procedure but its telling me theres either a driver installed, theres a problem with package removal or that X is running and using the driver. (Which is another thing, how do i get to a pure console with no X running!?!?)

each time the pc booted before i got a white screen with the nvidia logo, no however this is not the case. Are they installed and are they the latest ones, how do i tell? in windows i used to right click on the desktop and click settings.:???:

---

### Post by d1337 on 2006-02-07
[https://wiki.ubuntu.com/NvidiaManual?highlight=%28nvidia%29](https://wiki.ubuntu.com/NvidiaManual?highlight=%28nvidia%29) from the wiki is what I used...worked like a charm if you follow it step-by-step.  "Pure Console" as you worded it can be achieved by going to a terminal (ctrl-alt-f1), logging in and typing

sudo /etc/init.d/gdm stop

Hope this is of some help.

d1337

---

