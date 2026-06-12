---
title: "Please mail skype for Edgy"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by elexhobby on 2007-11-11
Could somebody please mail me the old version of skype (1.3.0.53 I guess). The new version doesn't work on edgy.. It gives the following errors..

The following packages have unmet dependencies:
skype: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is to be installed
Depends: libqt4-core (>= 4.2.1) but 4.2.0-1ubuntu6 is to be installed
Depends: libqt4-gui (>= 4.2.1) but 4.2.0-1ubuntu6 is to be installed
E: Broken packages

I searched a lot on the net and on torrent sites, but in vain.. I guess the only solution to this problem is to upgrade to Fiesty Fawn, which I would like to avoid as far as possible.. Hence I would be grateful if somebody could please mail me the skype package that would work on edgy.. My email is [email]elexhobby@yahoo.com[/email].

Thanks in advance..

---

### Post by jasmuz on 2007-11-11
Before doing anything, type in the command line:

sudo apt-get install -f 
(to fix your broken packages and clear dependencies, hopefully that will do it).

---

### Post by elexhobby on 2007-11-11
Hi..

Thanks for replying.. This is what I got after typing the command..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 168 not upgraded.

Believe me, I guess the only solution is to get the old package.. I had even tried manually installing latest versions of the above 3 packages (libasound, etc) However, they have their own set of dependencies, which again Edgy doesn't support..

---

