---
title: "Remote desktop for Ubuntu?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-07-10
I wish I could access my home Ubuntu desktop from my Windows-based office PC. Is there any remote desktop application for Ubuntu that could help me achieve this?

---

### Post by Rule on 2006-07-10
you can use freenx, i'm currently using it with no problems at all

[http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx](http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx)

---

### Post by raldz on 2006-07-10
I use VNC.. both my Ubuntu and Kubuntu has Desktop Sharing enabled which I can then access using VNC viewer for Windows..

---

### Post by zugu on 2006-07-10
However, my work PC is behind a router, and the admin there has restricted access to some ports (don't really know what ports).

So is there a way to make the VNC server listen to a standard (<1024) Windows port? If yes, how?

---

### Post by raldz on 2006-07-10
Ok your first option is to befriend your admin and tell him to forward port 5900 to your machine.. if not you may use SSH to tunnel traffic and pass the firewall.. here is the guide:

[http://www.realvnc.com/faq.html#firewall](http://www.realvnc.com/faq.html#firewall)

---

### Post by zugu on 2006-07-10
Thank you for the answers.

---

