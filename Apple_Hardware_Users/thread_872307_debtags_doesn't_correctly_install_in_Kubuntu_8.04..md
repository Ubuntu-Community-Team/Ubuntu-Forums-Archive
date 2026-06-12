---
title: "debtags doesn't correctly install in Kubuntu 8.04.1 PPC"
date: 2008-07-27
forum: Apple Hardware Users
---

### Post by HANtwister on 2008-07-27
I have a 300MHz Clamshell G3 iBook with me, and, as a random experiment, I tried installing Kubuntu 8.04.1 on it (the burned CD was verified with both the computer that burned it and the CD's own verification tool). The only issue during installation was as follows:

Setting up debtags (1.7.3ubuntu4) ...
No such file or directory. Context: opening index file /root/.debtags/vocabulary

dpkg: error processing debtags (--configure):
 subprocess post-installation script returned error exit status 1

This eventually causes all the following packages to reportedly fail installation because of the missing dependencies:

adept-common
adept-updater
adept
language-selector-qt
adept-installer
adept-manager
adept-batch
adept-notifier
kio-apt
kubuntu-desktop

The only symptom I can see from this is that Add/Remove Programs complains (and reasonably so); running apt-get install <above packages> fixes that, and debtags seems to install fine the second time around.

Otherwise, I'm still playing with it, but can anyone else see if they have the same issue?

Thanks, -HANtwister

P.S. Oh, yeah, I forgot to mention I was using the alternate CD.

---

### Post by wenzhi on 2008-08-02
:KSWelcome to view our website:[www.Jordan9.com](www.Jordan9.com)
Please contact e-mail:Jordan9@hotmail.com
we have some kinds of products to offer you see and choose.We hope to get  a good long business time with all customers all over the world.My products have a good quality , 
preferential benefit price and warm service,they very popular in the U.S.A.If you want 
to know further information , Please contact to us,We look forward to hearing you ,Have a Good Luck!:guitar:

---

