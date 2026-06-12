---
title: "My X froze up for no appearant reason"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-10-27
I try to go into Ubuntu, and it says my graphics X in not set up properly and in shuts itself down.  It happened overnight for some reason.  Any idea how to fix this?  PS I have the AMD64 system so it may be a factor
THX!:(

---

### Post by bulldog on 2006-10-27
```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

Give this a try.

---

