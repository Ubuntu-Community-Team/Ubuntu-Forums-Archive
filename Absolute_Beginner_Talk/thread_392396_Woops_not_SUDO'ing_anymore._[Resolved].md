---
title: "Woops not SUDO'ing anymore. [Resolved]"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by foldor on 2007-03-24
Yeah I did something pretty dumb without realizing it. I took my only user account and change its group using usermod -G instead of usermod -a. Yeah, now he is no longer able to do sudo or any administrative tasks. I was even dumb enough to disallow logging in as root. Well, I am able to use SU to log into root, so I can get the access back. But I need to know what terminal commands to use. 

Any help is appreciated,
Foldor

---

### Post by aysiu on 2007-03-24
This might help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by foldor on 2007-03-24
Yep, that helped me fix it.

Thanks!

---

