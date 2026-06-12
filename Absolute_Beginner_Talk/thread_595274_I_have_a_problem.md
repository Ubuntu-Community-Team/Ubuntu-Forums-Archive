---
title: "I have a problem"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mkamal30 on 2007-10-28
[B][B]May be I remove user from my system, and when try reloading  for system show me this message:-
the GDM group "gdm" does not exist. Please correct Gdm configuration and restart GDM. [/B][/B]

---

### Post by p_quarles on 2007-10-31
Try this:
```
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm restart
```
If that doesn't work, let us know what it says is wrong.

---

