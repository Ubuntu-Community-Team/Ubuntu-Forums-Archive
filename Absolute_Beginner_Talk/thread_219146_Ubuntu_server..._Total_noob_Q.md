---
title: "Ubuntu server... Total noob Q"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by pap3rtiger on 2006-07-19
hey i just installed ubuntu server, and im not really sure how to launch the gui.... or what gui its running, im migrating for the first time, please be nice..

---

### Post by aysiu on 2006-07-19
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by pap3rtiger on 2006-07-19
it says "couldnt find any package whos name or discription matched "ubuntu-desktop""

---

### Post by T700 on 2006-07-19
Did you run the update command first?

```
sudo aptitude update
```

Paul

---

### Post by pap3rtiger on 2006-07-19
> **T700 said:**
> Did you run the update command first?

```
sudo aptitude update
```

Paul

 yep. everything says done, no errors returned

---

### Post by steve.horsley on 2006-07-19
It could be difficult for us to figure out what's going wrong It may be quicker to just reinstall. Do NOT choose the server install - it is a minimal install as you would for a server that's destined to sit in a rack - no GUI.

---

### Post by pap3rtiger on 2006-07-19
and then i run the "sudo aptitude install ubuntu-desktop" line, 
intiializing package states....Done
couldnt find any package whoes name or description matched "ubuntu-desktop"

oh yea its running on an old IBM 325

---

### Post by pap3rtiger on 2006-07-19
> **steve.horsley said:**
> It could be difficult for us to figure out what's going wrong It may be quicker to just reinstall. Do NOT choose the server install - it is a minimal install as you would for a server that's destined to sit in a rack - no GUI.

that explains it, as i am runing ubuntu server 5.10...
wish i wuold have known there was no gui in that..

---

### Post by pap3rtiger on 2006-07-19
thanks for your help guys

---

