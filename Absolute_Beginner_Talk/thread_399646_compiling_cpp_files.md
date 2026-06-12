---
title: "compiling cpp files"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by wacind on 2007-04-02
Hi I am having some trouble compiling c++ files

I have used

**aptitude install build-essential**, I have also tried  **apt-get install build-essential **as well as synaptic both of which gave me the following error

> build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed

i have tried **apt-get -f** install and also the [B]apt-get update
[/B]
i have been searching for quite a while now but couldnt find anything to help me out 
i don't know if i have problems with my repositories

thanks 
wacind

---

### Post by zvacet on 2007-04-02
```
sudo aptitude install build-essentia
```

---

### Post by wacind on 2007-04-02
thanks but i already tried that but it won't install

gave me something to do with the following dependancy

> libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu12 is installed.



thanks
wacind

---

