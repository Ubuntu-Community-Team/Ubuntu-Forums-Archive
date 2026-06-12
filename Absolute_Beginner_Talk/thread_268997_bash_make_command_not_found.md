---
title: "bash: make: command not found"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-01
Um.. Small error here. I read a [guide to installing](http://www.monkeyblog.org/ubuntu/installing/) tarbells on ubuntu, and it tells me to run a make command after extracting my file. However, the terminal tells me that the command make is not found. What happened here? :lol: Thanks for the help~

---

### Post by po0f on 2006-10-01
UnknownVariable,

```
sudo atp-get install build-essential
```

---

### Post by UnknownVariable on 2006-10-01
For some reason my box is now rejecting a direct connection to my router... so I suppose I'll have to give it a go tomorrow (almost 3am here, lol). Thanks for the help though. :)

---

### Post by aysiu on 2006-10-01
You can install it off the CD, actually: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

