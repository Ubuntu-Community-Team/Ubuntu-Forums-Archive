---
title: "how to permanently modify $path?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-04-13
I noticed a program I deleted still has a path to it in my path variable.  How do I change the path variable, permanently?  I want to take away this particular path an also add a path to somewhere else. 

Thanks.

---

### Post by compmodder26 on 2007-04-13
Could be in different places.  I would first check the global profile files: /etc/profile, /etc/bash.bashrc, and /etc/login.defs.  If it isn't in there, check in ~/.bashrc or ~/.bash_profile.

---

