---
title: "Xserver"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by neozoid on 2007-09-18
Hi I'm newbie to linux.. ubuntu... i've download ubuntu 7.04 server edition.. just wanna know how do i start xserver

---

### Post by 505 on 2007-09-18
Not, X is not installed since it is a server. Servers are meant to serve, e.g. webpages are mail to clients. If you want a full graphical environment try to desktop edition. To install that on top of your server type:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by neozoid on 2007-10-05
i'm so sorry... i think i'm just to late to reply your msg... so thank you very much for helping me out

---

### Post by hyper_ch on 2007-10-05
well, a server is meant to server as explained above... so all possible resources should be free for the server to use. Tehre shouldn't be overhead programs that run... this dampers the performance.

Unlike Winodws with its central registry Linux has all configuration in seperate files. As server admin you don't need a gui to fix or alter anything and so, in order to gain performance, a server install is headless, meaning there's no gui to it.

---

