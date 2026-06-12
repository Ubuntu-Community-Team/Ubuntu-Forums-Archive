---
title: "Problems Updating"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jeremydostone on 2008-02-02
Hi
I Cant install any updates. When I try its gives me following error:

dpkg: failed to open package info file '/var/lib//dpkg/available' for reading: No such file or directory
E. Sub-process /usr/bin/dpkg returned an error code (2)
A package faild to install. trying to recover:
 
 And I cant install any applications in synaptic package manager.
If anyone knows whats wrong and like to reply that would be great.
Thanks

---

### Post by Martje_001 on 2008-02-02
Try
```
sudo dpkg --configure -a
```
in a terminal. What's the output?

---

### Post by jeremydostone on 2008-02-02
Still same 
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

---

### Post by p_quarles on 2008-02-02
Posts moved to a standalone thread.

---

