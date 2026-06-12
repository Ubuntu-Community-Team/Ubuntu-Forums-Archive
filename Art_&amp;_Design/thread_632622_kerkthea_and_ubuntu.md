---
title: "kerkthea and ubuntu???"
date: 2007-12-05
forum: Art &amp; Design
---

### Post by jrharvey on 2007-12-05
Has anyone heard of Kerkthea??? it is a really cool and free rendering program and I use it on windows but can't figure out how to install it for ubuntu. Has anyone tried this or know of another renderer that I can use that is as easy as this one?

---

### Post by smartboyathome on 2007-12-05
I looked at the kerkythea install and it looks like a typical compile/make/make install (but I am not on linux and cannot confirm this). Have you tried reading the README or INSTALL files?

---

### Post by jrharvey on 2007-12-05
I have never installed anything on ubuntu that wasnt in the repositories. I usually just use synaptic or add/remove. Haha, i know that sounds silly but i have gotten by without ever having to do this. I can't find any install instructions, thats why i asked. I installed in through virtualbox and surprisingly it rendered a very complex model of mine in less than 5 minutes. In my windows vista partititon it took about an hour with the same settings. I would really like to get it running natively on linux becasue i am sure it would do it even faster than virtualbox did.

---

### Post by oedipuss on 2007-12-06
Looking at kerkythea2007, version 1.4.1 (the only version offered for linux from their site) , there's no compiling needed. 
Just extract the folder somewhere and try to run the executable, from a terminal. 
```

cd Kerkythea  (or wherever you have extracted it)
./Kerkythea  (dot and slash mean run the executable located in the current dir, as opposed to trying to find one in /usr/bin or elsewhere)

```

Now, in gutsy it reported it couldn't find libpng.so.3 and libtiff.so.3 , that are files from libraries older than the ones installed. So :
```

cd /usr/lib
sudo ln -s libpng.so libpng.so.3
sudo ln -s libtiff.so.4 libtiff.so.3

```
which links the newer files to names looking like the older files. They seem to be compatible, and after that it seems to work.
Though for some strange reason compiz grays out the whole window thinking it's not responding, but it actually is responding.. If you see the same, you could try disabling the effect from compiz.

Hope that helped =)

---

### Post by jrharvey on 2007-12-06
The funny thing is that i tryed this in WINE and it is soooo fast. I am going to try to install the linux version just to test it out but I really don't have a problem using WINE if i have to. Thanks guys yall are awsome.

---

