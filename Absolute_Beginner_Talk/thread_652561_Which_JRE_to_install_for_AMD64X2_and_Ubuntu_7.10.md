---
title: "Which JRE to install for AMD64X2 and Ubuntu 7.10?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-12-28
Which version of JRE should I install for AMD64X2 and Ubuntu 7.10?  

Synaptic offers 
1.  JRE 5.0 32-bit  1.5.0.13 Oubuntu1
2.  JRE 5.0 Architecture Dependent Files  1.5.0.13 Oubuntu1
3.  JRE 5.0 Architecture Independent Files  1.5.0.13 Oubuntu1
4.  JRE 6 32-bit  6-03 Oubuntu2
5.  JRE 6 Architecture Dependent Files  6-03 Oubuntu2
6.  JRE 6 Architecture Independent Files  6-03 Oubuntu2

Can anyone tell me which version of JRE to install, and, since I want to learn everything I can, why that option is the best?

Also, are there any known problems about java with AMD64 and linux?

---

### Post by oldos2er on 2007-12-28
Are you running the 64-bit version of Ubuntu?

---

### Post by bettyhills on 2007-12-28
Yes.  AMD64 7.10 Ubuntu clean install from the live CD.

---

### Post by doorknob60 on 2007-12-29
Without installing a 32-bit version of firefox you can't run a JRE in 64-bit, but that will change when Java 7 is released. If you want to install the 32-bit Firefox there's a good guide on the ubuntu wiki, just google it.

---

### Post by Perfect Storm on 2007-12-29
You could go with icedtea if you want java in browser - though it's not perfect yet.

---

### Post by bettyhills on 2007-12-29
Folks, please advise. I completely destroyed FF 7.04 trying to install java and azureus and started over.  In the new clean install of GG7.10, azureus crashes with Java GCJ. 

I just want to install a stable version of java AND a stable version of azureus without bringing down anything else like Firefox (version Mozilla Firefox 2.0.0.11, Copyright (c) 1998 - 2007 mozilla.org).

I need to know what version of JRE to install and the same for azureus?  New to Linux, I do not know if I am allowed to install 32-bit software with a 64-bit Ubuntu installation.

Can anyone advise me**_ exactly_** what to do here?

---

### Post by Perfect Storm on 2007-12-29
If you want a torrent application I would suggest Deluge and it's not depended on java. Azureus is to heavy and buggy for my taste.

You need Sun Java 1.6 for Azureus
```
sudo aptitude install sun-java6-jre sun-java6-fonts sun-java6-bin ia32-sun-java6-bin
sudo update-alternatives --config java 
```

Choose sun java jre 1.6

---

### Post by bettyhills on 2007-12-29
Thanks for the advice on Deluge.  I installed and it is working beautifully.

---

