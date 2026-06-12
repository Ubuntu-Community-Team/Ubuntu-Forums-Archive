---
title: "cannot install wine"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by forgetso on 2007-09-04
Hi,

For some reason i cannot use wine.  I can install it but every time I try to run winecfg or any .exe application with wine the entire system crashes.  I have now tried wine with feisty fawn (64-bit and 32-bit) and the same freezing up occurs each time.

My system comprises of an AMD Athlon 64-bit CPU and a KV-8 Pro Motherboard.  Fairly standard.

What could possibly be the problem?

Cheers

---

### Post by forgetso on 2007-09-04
Sorry, I meant I cannot run wine.  Not "Cannot install wine".  I have installed it from application manager and from source many times.

---

### Post by mc4man on 2007-09-04
What if any error message(s) are you seeing in the terminal while running winecfg?
Do you have a .wine folder ?
```
I have installed it from application manager and from source many times.
```
why many times (if same pc/installation)
have you successfully run winecfg on this install? (at least once)

may help can't hurt
```
wineprefixcreate
```

---

### Post by forgetso on 2007-09-05
> What if any error message(s) are you seeing in the terminal while running winecfg?

I do not get as far as any error messages.  The entire system crashes, the mouse pointer freezes and any music that is playing begins to skip over and over.

> Do you have a .wine folder ?

After restarting I do have a .wine folder which i then removed before I tried to install again.

I have tried to install many times as it has never worked.

> have you successfully run winecfg on this install? (at least once)

I have never managed this

> may help can't hurt
Code:

wineprefixcreate

I tried this last night and again the system just froze.

I don't kow if this will help or not but I have AMD athlon 64, KV-8 Pro MB and a Radeon 9700 128Mb graphics card.  I have tried to run wine on fresh installs of both the 32-bit and 64-bit versions of ubuntu 7.04

---

### Post by forgetso on 2007-09-06
please can someone help me with this. i am at my wits end

---

### Post by WebSiteGuru on 2007-09-06
what version is wine?

---

### Post by forgetso on 2007-09-06
i have tried with 0.9.44 and 0.9.33. i currently have 0.9.44 installed

---

### Post by WebSiteGuru on 2007-09-06
9.44 should work fine. 

Hmmm! How much memory do you have?

And are you running anything else that take up a lot of memory?

---

### Post by philinux on 2007-09-06
You need to run from Application > Accessories 

Chose Wine File.

---

### Post by WebSiteGuru on 2007-09-06
> **philinux said:**
> You need to run from Application > Accessories 

Chose Wine File.

Hmm, I never actually seen it in 9.44 version. Isnt it supposed to be commandline only (since 9.39 version)?

---

### Post by philinux on 2007-09-06
I'm now using the repo version 9.33 cos 9.44,from winehq, did not have this in the menus. So much for newer versions.
You can just type winefile from the terminal ,browse to your exe and double click.

---

### Post by WebSiteGuru on 2007-09-06
I thought about that myself, reverting to 9.33 in the repo. Don't know if that is worth it.

---

### Post by philinux on 2007-09-06
I wonder which version Gutsy will have?

---

### Post by WebSiteGuru on 2007-09-06
The best one I hope. Still I dont know which is the best one. :lolflag:  Still having problem with getting it just right.

---

