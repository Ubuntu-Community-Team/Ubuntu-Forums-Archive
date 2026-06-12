---
title: "Wine"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-07-02
I can't get wine to work. Everything says I have it installed I just can't find it. I tried sudo apt-get install wine but it says it is already installed. Where could it be?

---

### Post by supersonicdarky on 2007-07-02
try this
```
winecfg
```
to configure wine (and see if its actually installed)

then once done, navigate to folder with exe you want to run and type
```
wine *filename*.exe
```

---

### Post by robertc36 on 2007-07-02
The wine configuration is at system/Preferences/Wine Configuration.
Got this link ; [http://frankscorner.org/](http://frankscorner.org/)   
Here the other day, had no clue until then but have foobar running now.

---

### Post by Istonian on 2007-07-02
It is installed, but when I go to install something like how you said it says module not found. Here is an example.

c:\\windows\\system32\\Install_WLMessenger.exe": Module not found

---

