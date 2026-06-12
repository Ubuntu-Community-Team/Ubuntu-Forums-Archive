---
title: "X-server failure HELP"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by bramsundar on 2007-06-16
I tried to upgrade my feisty gui with beryl, following the instructions from [http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html]("http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html") but after I installed the nvidia glx, the x-server failed, and I can't start my gui anymore. Can somebody please help me??

---

### Post by w4ett on 2007-06-16
try resetting x by using :

sudo dpkg-reconfigure xserver-xorg

---

### Post by bramsundar on 2007-06-16
Thanks a lot for the reply, but I managed to fix the problem by reinstalling the x server package. Everything is going fine now :p

---

