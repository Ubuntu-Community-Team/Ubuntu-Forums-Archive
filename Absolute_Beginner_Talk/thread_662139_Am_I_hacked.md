---
title: "Am I hacked?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by wormser on 2008-01-08
Here are the rusults of rkhunter.

> /usr/sbin/xinetd                                   [ **[COLOR="Red"]Warning[/COLOR]** ]


I have never had that warning before.  It is different than the normal false positives.  Any ideas on what I should look into to finding the source?  What are your thoughts?

---

### Post by blithen on 2008-01-08
I'm sure it's a false positive, I wouldn't worry, you can remove it by doing
```
sudo apt-get remove xinetd
```
If you get to worried about it.

---

