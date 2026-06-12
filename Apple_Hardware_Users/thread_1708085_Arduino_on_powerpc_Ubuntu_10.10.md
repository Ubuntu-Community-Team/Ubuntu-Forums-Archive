---
title: "Arduino on powerpc Ubuntu 10.10"
date: 2011-03-16
forum: Apple Hardware Users
---

### Post by teachop on 2011-03-16
At the present time, you can select the Arduino package in the repos, but it won't actually install due to a dependency problem for powerpc only.

This is the *wrong way* but if you grab librxtx-java_2.2pre2-8_powerpc.deb from Debian and install that, then Arduino will install from Synaptic fine.  And it works fine (version is a bit stale).

(Random Tip change .arduino/preferences.txt to set editor.antialias=true)

---

