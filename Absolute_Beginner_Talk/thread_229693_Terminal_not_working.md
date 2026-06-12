---
title: "Terminal not working?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by ophanim on 2006-08-04
Long time windows user trying my hand at linux again.  I'm having a few very odd problems and I'm not sure what's going on.  I've tried the search feature and gone a few pages deep, but can't turn up anything similiar to my situation.

1.  When I use terminal, I simply select it by going Applications -> Accessories -> Terminal.  This brings up "GNOME Terminal 2.14.2".  However, anytime I try to use "make" (to isntall something manually), I get this as a return:

bash: make: command not found

Ugh!

2.  I've got a 520 Dlink wifi card in my dell.  I can connect to the internet and *assume* that the madwifi drivers are installed.  However, wlanconfig in terminal returns:

bash: wlanconfig: command not found

That keeps me from turning on monitor mode on the card.  Ugh x2!  I'm not sure how to check what driver my wifi card is using, exactly, and because I can't use "make", I haven't been able to manually install the madwifi drivers just to be safe.  

I'm sure I'll have more problems.  Thanks in advance for any help.

---

### Post by aysiu on 2006-08-04
If you don't have your internet set up yet, add the CD as a repository: ```
sudo apt-cdrom add
``` Then refresh your sources: ```
sudo aptitude update
``` and install *build-essential*
```
sudo aptitude install build-essential
``` Then try your *make* command again.

---

### Post by FizDev on 2006-08-04
1. Just type in a terminal
```
sudo apt-get install build-essential
```

---

### Post by ophanim on 2006-08-04
build-essential worked, thanks!

The next problem:

I'm following the newbie how-to on madwifi.org.  In the user docs, they mention a problem similiar to mine, but I seem to be missing something entirely..

```
ophanim@ship:~/Desktop/madwifi-0.9.2$ make
/bin/sh: line 0: cd: /lib/modules/2.6.15-26-386/build: No such file or directoryMakefile.inc:89: *** /lib/modules/2.6.15-26-386/build is missing, please set KERNELPATH.  Stop.
ophanim@ship:~/Desktop/madwifi-0.9.2$

```

.. my /lib/modules/2.6.15-26-386/build is missing?  :-(

---

