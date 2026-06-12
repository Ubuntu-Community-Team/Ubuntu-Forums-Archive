---
title: "How to install partimage-0.6.6.tar.bz2"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-17
I followed the instructions which saya:
Once you have downloaded partimage-x.y.z.tar.bz2, you must uncompress and compile:

 * Here is how to uncompress the sources: 

tar xfjp partimage-x.y.z.tar.bz2

* Now, you must compile: 

./configure --prefix=/usr && make && make install

But no luck.
THANKS

---

### Post by infurnus on 2007-11-17
Your running 3 commands at once run them individually and see if you cant find the problem after
```

./configure --prefix=/usr 

```
then run
```

make

```
Then once this is finished look to see if it resolved all dependencies  making sure you have all the files necessary to compile.

BTW what your looking for is in Synaptic Package Manager.

---

### Post by jmfa59 on 2007-11-17
THANKS
Never thought it is in synaptic I installed it now I have another problem I don't see in the menu where could it be.

---

### Post by infurnus on 2007-11-19
run this
```

alacarte

```
i changed mine but if it buggers for premissions you may wanna try sudo i probably chmod'ed the file for no good reason but this is the menu editor look for this program if you dont have it installed in synaptics

---

