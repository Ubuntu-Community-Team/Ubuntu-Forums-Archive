---
title: "Wine"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by hcwegge on 2008-02-27
Hi. I have just installed Ubuntu Gutsy 7.10 64 bit and I'm having trouble with installing WINE...
I can download the libraries but when I get to the part of the installation(from WINE's homepage) where I have to "apt-get install wine" it can't do it because it says it has some dependencies:

ia32-libs (says it can't be installed)
lib32asound2 (says it can't be installed)
libc6-i386 (says it can't be installed)

Can someone please help me getting WINE to work?? It really would mean a lot!!

Also... It seems that I can't install quite a few applications from the "add-remove" part because either the program I'm trying to download will "interfere with another program" or because of my computer type... Is this beacause it's 64 bit and the programs are made for 32 bit??

Any help or suggestions are more than welcome! 

Thanks!

Hans Christian Wegge

---

### Post by PmDematagoda on 2008-02-27
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Oldsoldier2003 on 2008-02-27
> **hcwegge said:**
> Hi. I have just installed Ubuntu Gutsy 7.10 64 bit and I'm having trouble with installing WINE...
I can download the libraries but when I get to the part of the installation(from WINE's homepage) where I have to "apt-get install wine" it can't do it because it says it has some dependencies:

ia32-libs (says it can't be installed)
lib32asound2 (says it can't be installed)
libc6-i386 (says it can't be installed)

Can someone please help me getting WINE to work?? It really would mean a lot!!

Also... It seems that I can't install quite a few applications from the "add-remove" part because either the program I'm trying to download will "interfere with another program" or because of my computer type... Is this beacause it's 64 bit and the programs are made for 32 bit??

Any help or suggestions are more than welcome! 

Thanks!

Hans Christian Wegge

try here:
[http://wiki.winehq.org/](http://wiki.winehq.org/) for latest wine info and distros. and:
[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)for more info how to get Wine working under 64bit Ubuntu distros

---

