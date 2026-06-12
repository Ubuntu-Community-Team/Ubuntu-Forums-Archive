---
title: "install gcc"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by DTMF on 2006-11-01
Hello ppl!I'm really really new at this so forgive me if my question is silly!
I want to install an ADSL usb modem but i can't get it done cause it says i don't have gcc compiler installed...I found an executable but it won't open...I'm used to double-clicking and automatically installing the application, so I guess that's not the deal here:p 
Could someone help?:confused:

p.s. I've installed ubuntu 5.10

---

### Post by jaboua on 2006-11-01
5.10 is a bit old, you should consider upgrading...

However:
```
sudo aptitude update
sudo aptitude install build-essential
```

That should install basic utilities needed to compile like gcc, make etc

---

### Post by DTMF on 2006-11-01
thank you very much!gcc is installed unlike my modem! :P
i'll surely upgrade it as soon as i have the whole dsl thing figured out!thanks!

---

