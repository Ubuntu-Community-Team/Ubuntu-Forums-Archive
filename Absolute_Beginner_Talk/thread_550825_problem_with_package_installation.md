---
title: "problem with package installation"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by yangkuan81 on 2007-09-14
Hi, Guys,

I am new to linux and got a lot of questions. But the first thing I want to ask is whether there is a way to install a package and all other packages it depends on together?
When I was trying to install something in Synaptics, it won't allow me because some dependencies are not met. And then, I have to go install those packages first, then those packages depends on some other packages. So it is like a chain of packages I need to install. Really really annoying. I bed there is a smart way of doing this and I just don't know yet.

Thanks for your time!

K

---

### Post by SOULRiDER on 2007-09-14
Synaptic WILL install those dependencies and dependencies of dependencies and so forth.... can you tell us what it was you were trying to install?

Try using aptitude to install it and see if you get any errors. Open a Terminal and type:
```
sudo aptitude install <package>
```

---

### Post by yangkuan81 on 2007-09-14
I was trying to install libgtk 2.0, then it says it won't install because libpango and libcairo are need but not installed. And then, when I try to install libpango, it says something else is not installed so it can't get installed... I will try the command you provided tho. Thanks!!!!!

---

### Post by SunnyRabbiera on 2007-09-14
yeh sometimes synaptic is fidgety, but please keep in mind to take care what you install...
Why do you need libgtk 2.0 for, are you a developer?

---

