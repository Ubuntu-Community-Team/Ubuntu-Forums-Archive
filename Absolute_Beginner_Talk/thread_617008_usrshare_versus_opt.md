---
title: "/usr/share versus /opt"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by BigFlatBrook on 2007-11-18
Are there conventions for putting applications in /usr/share versus /opt?

---

### Post by stido on 2007-11-19
Ubuntu/Debian usually leaves /opt empty and put things in /usr/share

/opt is mostly used for "desperate" cases where the apps don't conform with debian file system hierarchy.

most of the times, all major linux distros abiding to the POSIX standards use /usr and leave /opt for 3rd party apps outside the realm of posix.

EDIT:
[perhaps this would explain]("http://www.pathname.com/fhs/") a bit about posix filesystem hierarchy

---

