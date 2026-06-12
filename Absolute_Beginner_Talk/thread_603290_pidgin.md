---
title: "pidgin"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by azurelight1337 on 2007-11-05
alland@allan-desktop:~$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance

I had installed Pidgin before Gutsy and now it doesn't work.

---

### Post by dpar on 2007-11-05
Try reinstalling.

---

### Post by Jimmyfj on 2007-11-05
Delete the pidgin folder /usr/local/lib (and all instances of libpurple.so) as well as those in /usr/local/ and reinstall it (pidgin that is)

Hope that helpes you out.

---

