---
title: "Yet another ATI driver question!!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Parms on 2007-08-20
Has anyone succesfully have any luck finding drivers that work with:

ATI Radeon Xpress 200M

If so where can I find them, and is there a program or script that can do it for me. I'm a n00b and wouldn't know the first clue how to.

I'm assuming I have a driver because I can load into ubuntu 7.04 64bit just fine...

Problem I'm having is loading compiz... says my system is not supported. I'm assuming this is because my graphics card driver isn't correct..

All I did was goto
System >> Administration >> Restricted Drivers Manager

I clicked enabled and it popped up a window installing.. the drivers I assume. Now it says enabled and in use... but how do I know it works for 3D acceleration. 

I would like to get it to run compiz, and then eventually start geting my 3D games running.
Any help would be appreciated. Thanks in advance.

Don't know if this helps o not (for the compiz part... 

parms@parms-laptop:~$ compiz
Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$

---

### Post by Hobo Joe on 2007-08-20
Download [this]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb"). Then open it(it should be on the desktop).

Run this command:
```

envy -g

```
Then press 'install ATi driver'. Let it configure your xorg.conf for you.

---

