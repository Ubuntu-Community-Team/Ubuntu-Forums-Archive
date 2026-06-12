---
title: "[SOLVED] compiz won't load on my vostro 1000?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by drazgo on 2008-03-22
hi everybody, 

I'm having some issues setting up compiz-fusion on my Dell vostro 1000 (with ATI Radeon Xpress 200). I use the restricted driver provided by (k)ubuntu. When i use the command 'compiz --replace' in my terminal as i have been told in this thread: 

[https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-7a9f69c5895967a3652f8b5bee8bc50d96df852b](https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-7a9f69c5895967a3652f8b5bee8bc50d96df852b)

it gives me this error: 

> Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

please help!!! 
Drazgo

---

### Post by jan quark on 2008-03-22
try this

```
sudo apt-get install xserver-xgl
```

and change the session during login to xclient 
now you should be able to activate the effects

---

### Post by drazgo on 2008-03-23
thanksss! that did the trick! xD

---

