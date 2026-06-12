---
title: "I love you guys :) and I need more help :)"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Frogsmasher on 2007-11-03
I have not been on this site long, and (not knowing very much about linux at all) all I have asked are questions. But being the good sports you guys are I have another one for you

I have a Ti-86 calculator with a homemade serial port connector. I got Tilp to run in and ran into my problem trying to install it. Okay I got the error:

configure:5353: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

So I did and all the config.log does is RELIST THE ERROR go figure no help at all lol so I was hoping you guys could help me find my way... again.

---

### Post by Wiebelhaus on 2007-11-03
I like frogs.



But a sanity check from my understanding is a check to insure you are root , maybe you need to grant higher permissions?

---

### Post by Frogsmasher on 2007-11-03
For now there is only one account I am root, or should I say "I AM GOD of my personal copy of ubuntu." lol

---

### Post by Frogsmasher on 2007-11-03
I tried a variant the install guide suggested using sh ./configure instead of just ./configure but got the same problem, I also tried to just go on and it did not work.

---

### Post by Wiebelhaus on 2007-11-03
> **Frogsmasher said:**
> I tried a variant the install guide suggested using sh ./configure instead of just ./configure but got the same problem, I also tried to just go on and it did not work.

sudo sh?

---

### Post by Frogsmasher on 2007-11-03
i tried:

sudo ch ./configure

got the same problem again :(

---

### Post by Frogsmasher on 2007-11-03
Oh well I have to go to bed, if you give an answer I will after work (3:00) tomorrow.

---

### Post by SOULRiDER on 2007-11-03
Youve installed compilers right?

```
sudo aptitude install build-essential checkinstall
```

---

