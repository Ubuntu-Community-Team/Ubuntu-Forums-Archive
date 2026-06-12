---
title: "webcam"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by natman on 2007-04-22
I have a HP pav dv2000 with built in webcam, i can use it when i use a program called "ekiga" but any of my IM clients dont see it, can anyone help?

---

### Post by silverglade00 on 2007-04-22
I have a dv2000 series laptop also. From the information I have found, it is mainly a problem of applications haven't updated yet. Webcams use software called Video4Linux (v4l) to run. Our webcam uses v4l 2.0, as does Ekiga. The problem is that pretty much every other software out there that can use a webcam is using v4l 1.0. So, basically, we are stuck waiting for the software to catch up.

BTW, at least it works now. About a year ago, it required all kinds of kernel patches and compiling to get the webcam to even turn on.

---

### Post by natman on 2007-04-22
Somehow i had that feeling, maybe by the next kernel update we will have peace thanks for the reply.

---

