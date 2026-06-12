---
title: "Cant register on Arch Forums"
date: 2013-01-26
forum: Any Other OS
---

### Post by kevdog on 2013-01-26
I've been trying to register on Arch forums but the captcha always gets me:

date -u +%V$(uname)|sha256sum|sed 's/\W//g'

Right now the first part (date -u +%V(uname))

gives me 
04Linux

Is this correct and why isn't it working?

---

### Post by trent.josephsen on 2013-01-26
That's what I got, running Arch at the moment. The value to put in the captcha should start with e06135... Is that what you tried?

---

### Post by sffvba[e0rt on 2013-01-26
AFAIK you could just enter it into terminal and then copy paste the result?!


404

---

### Post by CharlesA on 2013-01-26
> **not found said:**
> AFAIK you could just enter it into terminal and then copy paste the result?!


404

This.

It is meant to be run as a whole command, not in parts, which is why the pipes are there.

---

### Post by kevdog on 2013-01-26
It finally worked -- I have no idea right -- about the 20th time I entered the password it finally worked -- I didn't do anything different the 20th time but whatever.  Thanks guys for answering.

---

### Post by Habitual on 2013-01-27
I ran ```
date -u +%V$(uname)|sha256sum|sed 's/\W//g'
``` in terminal and got:
```
e06135132a9bf3778b771cae11f072d7e59cf9d03494e9fb7113c84a1cbd8876
```

your output should be similar?

---

