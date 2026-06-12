---
title: "RealPlayer 10 does not spawn window"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by clevin on 2007-04-21
I tried two different way to install it.

a *.bin from real website
a *.deb from the search of this forum

in both situation, it was installed without any problem.

but when I click the realplayer icon, nothing happen? whats wrong?

---

### Post by taurus on 2007-04-21
Try to run it from a terminal to see what the error message is.

```
realplay
```

---

### Post by clevin on 2007-04-21
i reinstalled the *.bin
and I went into Realplayer's directory
I did ./realplay
this is what I got
> ./realplay: line 75: 24961 Segmentation fault      (core dumped) $REALPLAYBIN "$@"

---

### Post by clevin on 2007-04-21
solved, another sin of SCIM. I added this
> export GTK_IM_MODULE=xim 
right below first line (#!/bin/sh) in the file **realplay**

just had to do the same for my Thunderbird 2.0, why SCIM sucks so much?

---

### Post by lukesh13 on 2007-04-21
Thx a lot !!!
I got the same problem, and now it works perfect !!

---

