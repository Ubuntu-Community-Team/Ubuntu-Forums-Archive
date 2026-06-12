---
title: "[SOLVED] changing usplash"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by SurlyDune on 2008-04-07
i'm trying to change my usplash using SUM but when i try and look for my downloaded uspalsh i can't find it and SUM doesn't let me look in places other than root and i cant place my uspash in there. where do i have to save my usplash file so i can select it using SUM?

---

### Post by SurlyDune on 2008-04-07
nevermind i got it, just getting used to ubuntu so i didnt realize i could drag and drop

---

### Post by stchman on 2008-04-07
> **SurlyDune said:**
> i'm trying to change my usplash using SUM but when i try and look for my downloaded uspalsh i can't find it and SUM doesn't let me look in places other than root and i cant place my uspash in there. where do i have to save my usplash file so i can select it using SUM?

Startup manager does not change the usplash.  To do that install the usplash package.

```
sudo apt-get install usplash
```

SUM will allow you to change the boot splash.

Usplash files are in the following location:

/usr/share/pixmaps/splash/

---

