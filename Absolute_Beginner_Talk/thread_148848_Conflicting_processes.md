---
title: "Conflicting processes"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by The_Tankengine on 2006-03-22
I keep getting the error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I am trying to run apt-get update.  What else could be running?  Do I have to change the permissions on the ~/lock folder?

Any help is appreciated!

---

### Post by linear on 2006-03-22
Do you have Synaptic or another package manager running at the same time?

---

