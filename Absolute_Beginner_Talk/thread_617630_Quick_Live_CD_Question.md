---
title: "Quick Live CD Question"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Stavro on 2007-11-19
Hi there, how do you access the root user folder from a liveCD?

---

### Post by hollaburoo on 2007-11-19
If you mean the root user folder in the livecd's filesystem, then ```
gksudo nautilus /root
```

If you mean the root user folder for the computer the live cd is running on, then first you'll need to mount the hard drive of that computer, then ```
gksudo nautilus [mount point]/root

```
In general the root user isn't used at all on ubuntu though, instead we use sudo for root priveleges

---

