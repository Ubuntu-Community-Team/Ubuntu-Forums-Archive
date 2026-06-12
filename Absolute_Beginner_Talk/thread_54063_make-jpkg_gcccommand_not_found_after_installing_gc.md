---
title: "make-jpkg gcc:command not found after installing gcc 3.3"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by supanova on 2005-08-03
Hi All

I noticed that only gcc-3.3-base was installed so I installed gcc-3.3 which is supposed to be the actual C compiler

When running make-jpkg (trying to get SUN JDK1.5 installed), it says

```
sh: gcc: command not found
```

Well I can't find it either.... only gcc-3.3.... which does make sense...

I suppose when installing gcc (I used synaptic) it does not create the symlinks and modify the paths etc?..... 

Is their a recommended method to install gcc including changes to the shell profile for a user etc...

Sorry for this stupid question

Thanks

---

### Post by Knome_fan on 2005-08-03
apt-get install build-essentials should give you all what you need to get started.

Also there is a java package in the ubuntu backports extras repository, iirc.
Add the following to your /etc/apt/sources.list
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

---

