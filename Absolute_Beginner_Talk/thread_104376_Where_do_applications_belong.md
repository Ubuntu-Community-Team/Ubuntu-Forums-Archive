---
title: "Where do applications belong?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Noah0504 on 2005-12-16
I downloaded BitTorrent 4.2.1 and extracted it.  It runs fine, but I was wondering where I should put it.  I don't really want it sitting around in my Home folder, but I'm not really sure where applications go in Linux.

---

### Post by mherring on 2005-12-16
Short answer:  Anywhere you want.

Long answer:  There are various conventions.  The core stuff is generally all in /bin or /sbin.  Things used more by ordinary users are in /usr/bin, /usr/local/bin, and more.
A lot of stuff added without using the distro's installer are in /opt.

---

### Post by joshuapurcell on 2005-12-16
It depends on the individual user, really. I like to know where programs supposed to go as well, but as soon as I say "everything on the system is getting installed in /usr/local" then an application comes around that wants to be installed in the /opt directory. This is what I try to do now:

-If a program is pre-compiled/binary, then I put it in the /opt directory. Programs like this are: Eclipse, IBM applications, Limewire,etc.

-If I'm compiling a program, then I put it in the /usr/local directory. This includes: mysql applications, all apache programs (geronimo, tomcat), etc.

-All games get installed in my home directory.

The above isn't how it is *supposed* to be though... it's just one way of doing it. It is really up to you where you want the programs to be. If your system is a single-user computer for the most part, then you can never go wrong installing things in your home directory. This would eliminate the  need to set the correct permissions on directories (since you would have access by default) and it would keep everywhere else on your computer relatively clean.

---

### Post by Noah0504 on 2005-12-16
haha, It's good to know Linux doesn't really care, but I suppose other OS's don't either...

Anyway, I stuck it in /opt.  Thanks for the help.  :)

---

### Post by UphillSkier on 2005-12-16
[QUOTE=Noah0504]I downloaded BitTorrent 4.2.1 and extracted it.  It runs fine, but I was wondering where I should put it.  I don't really want it sitting around in my Home folder, but I'm not really sure where applications go in Linux.[/QUOTE]
The linux documentation project at [http://www.tldp.org/](http://www.tldp.org/) has a wonderful variety of general guides to linux.  Have a look at the Introduction to Linux. [http://tldp.org/LDP/intro-linux/html/index.html](http://tldp.org/LDP/intro-linux/html/index.html)   It covers lots and lots of stuff that you really need to know to take linux seriously.   It's worth the investment, because linux really is great. 

best wishes

---

