---
title: "New to Ubuntu"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by siminone on 2006-01-28
Hi, I have just switched over from Mandriva and this is the first chance I've had to have an indepth look of seeing what's in Ubutnu.

While overall I am impressed, I found a few niggly things like unable to play DVD's and missing environment paths.

I'll get those sorted out once I get the time but there are a few things I would be grateful if someone could please provide answers to.

Firstly, MDV's latest release had an interactive firewall that detected unathorised accesses. Is there something similar for Ubutunu?  

On the subject of security, how secure is it and how can I make it more so?

Lastly, as Debian.org .Deb depository is down for the time being, is there any alternative sites? I've being doing web searches for certain packages and haven't had much success, i've had to convert RPM's.

Thanks in advance

Alsa

---

### Post by gila_monster on 2006-01-28
Welcome to Ubuntu.

The only firewall with which I have experience is Firestarter. It is actually a front end to iptables. It seems to work well, but may lack some of the fancier features of other firewalls.

Ubuntu by default has all incoming ports turned off, so it is pretty secure out of the gate. If you are going to open those ports, you'll almost certainly want a firewall up. But if not, you probably don't need one.

I can't address your other questions. I'm relatively new to Ubuntu myself.

gm

---

### Post by HJThis on 2006-01-28
Hello,siminone & Welcome

Well as was said go with Firestarter

now here is a prog that makes installing items
not hard at all just put a check mark in the boxes
of items you want to install & just click OK

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

& this link here has tons of info & how tos

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

now the first items you should install are

Firestarter

chkrootkit

rkhunter

you can just goto System >> Adminstration >> Synaptic Package Manager
& just type in the above progs & it will install them for you

then

sudo rkhunter -update

sudo rkhunter -c --skip-keypress

sudo chkrootkit

Best of luck

---

### Post by siminone on 2006-01-28
Thanks gila_monster, so far I like what I see with Ubuntu, I couldn't believe how good Gnome is. I've always been a fan of KDE but I've changed my mind. 

I've been with Mandriva since 9.0 but  I was  in two minds of renewing my subscription especially since it is a commerical operation that is only making money on it's server rather than desktop software and the noticable QA issues with the 2006 release and this has made me look elsewhere.

I'm really paranoid about security, is iptables already setup? I don't see it saying anything during bootup?

---

### Post by siminone on 2006-01-28
thanks HJThis, only chkrootkit was in package, I can't download rkhunter due to connection error and had to downloaded firestarter RPM but when I run it, the message saying I have insufficent privilages to run it.

When I run it from the command line I get the following error message:

------------------------------------------------------------------------------------------------------
A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.
------------------------------------------------------------------------------------------------------

This comes up both under sudo and under root user

---

### Post by siminone on 2006-01-30
I updated the source packages and got all packages installed.

I also managed to figure out problem with enviornment variables. The problem was occurring when I was trying to compile source files. The solution was to make links of c compilers to gcc to g++ and it has worked.

---

