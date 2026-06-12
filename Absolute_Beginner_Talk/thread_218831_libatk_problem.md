---
title: "libatk problem"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by dwele on 2006-07-19
While installing in terminal libatk1.0-dev_1.12.1-1_i386.deb by```
dpkg -i
``` i have something like this: ```
root@dwele:/home/dwele/Desktop# dpkg -i libatk1.0-dev_1.12.1-1_i386.deb
(Reading database ... 77695 files and directories currently installed.)
Preparing to replace libatk1.0-dev 1.11.4-0ubuntu1 (using libatk1.0-dev_1.12.1-1_i386.deb) ...
Unpacking replacement libatk1.0-dev ...
dpkg: dependency problems prevent configuration of libatk1.0-dev:
 libatk1.0-dev depends on libatk1.0-0 (= 1.12.1-1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
dpkg: error processing libatk1.0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libatk1.0-dev
```

What to do?

---

### Post by mattisking on 2006-07-19
Where did you get that deb? The version of libatk you have on your system is newer than the dev version you are trying to install. Did you run synaptic? It's most likely the dev version of the current package is already available for you in synaptic.

---

