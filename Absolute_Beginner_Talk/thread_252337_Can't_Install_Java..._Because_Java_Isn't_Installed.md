---
title: "Can't Install Java... Because Java Isn't Installed?!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Dragonreaver on 2006-09-06
Ok, so this is confusing me.

I downloaded the java JRE package (sun-java5-bin_1.5.0-06-1_i386.deb). But when I try to install it, I couldn't, because:

> Error: Dependency is not satisfiable: sun-java5-jre

I located a package called sun-java5-jre. So I tried to install that...

> Error: Dependency is not satisfiable: sun-java5-bin

...ok. So the bin can't install because the jre isn't, but the jre can't install because the bin isn't?!

Screw chickens and eggs... What came first, the bin or the jre? :-k 

Can someone not quite as stupid lend me a hand? T'would be much appreciated.

---

### Post by whizbaby on 2006-09-06
Try selecting the packages in synaptic. Anything changes? (did you apt-get update?)

---

### Post by Dragonreaver on 2006-09-06
I didn't install them via Synaptic because I couldn't find them. I got them from packages.ubuntu.com

I still can't find them in Synaptic :\ (I did apt-get update anyway though)

---

### Post by Jagot on 2006-09-06
Java is in the multiverse repository which is not enabled by default.  See either of these methods to enable:

[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then from Terminal:

```
sudo aptitude update
sudo aptitude install sun-java5-bin
```

---

### Post by xpod on 2006-09-06
Automatix is handy for those bits n bobs too

---

### Post by Dragonreaver on 2006-09-06
Edit: Ignore. It randomly decided to work ¬_¬ I'll see how this goes :) Thanks.

Edit2: Yaaay. It worked fine that time. Thanks guys :D

---

### Post by Zaid on 2006-09-07
Thanks

---

