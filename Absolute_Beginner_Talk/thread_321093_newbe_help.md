---
title: "newbe help"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by troll380 on 2006-12-18
Port 4662 is not available!

This means that you will be LOWID.

Check your network to make sure the port is open for output and input.
how do i fix this  please?

---

### Post by taurus on 2006-12-18
Check your router to make sure you open that port for incoming/outgoing traffic!!!

---

### Post by troll380 on 2006-12-18
ok i dont have a router
im on a 1 box conection with a  comcast cable modem

---

### Post by taurus on 2006-12-18
Then maybe the iptables blocks that port.  Install firestarter and use that to open it then...

```
sudo aptitude update
sudo aptitude install firestarter
```
It should be in System -> Administration -> Firestarter.

---

