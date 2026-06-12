---
title: "please help me in installing Xine from sorce"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by jomon_johnson on 2006-12-30
i downloaded xine and xine lib source.and when i gave configure their are some error message.I think it is because their is no gcc installed.What i should do to install xine
With Respect.please help me
Jomon Johnson

---

### Post by taurus on 2006-12-30
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```
You have to build and install xine-lib first before you can build and install xine...

---

### Post by pseudonym on 2006-12-30
> **jomon_johnson said:**
> i downloaded xine and xine lib source.and when i gave configure their are some error message.I think it is because their is no gcc installed.What i should do to install xine
With Respect.please help me
Jomon Johnson
Why are you compiling from source when there are recent versions of libxine and 3 or 4 xine frontends in the Ubuntu repositories??

---

