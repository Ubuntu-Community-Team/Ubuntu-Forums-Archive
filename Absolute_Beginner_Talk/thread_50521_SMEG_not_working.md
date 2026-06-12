---
title: "SMEG not working"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-20
I tried now to install smeg with the command:

sudo apt-get install smeg

The following errors jumps up.

[QUOTE]
The following packages have unmet dependencies:
  smeg: Depends: python (>= 2.4) but 2.3.4-1ubuntu1 is to be installed
        Depends: python2.4-gtk2 (>= 2.6) but it is not installable
        Depends: python2.4-libxml2 (>= 2.6.17) but it is not installable
        Depends: python-xdg (>= 0.14) but 0.8-1 is to be installed
        Depends: python2.4-glade2 (>= 2.6) but it is not installable
E: Broken packages
[QUOTE]

Why does it gives me this? I have activated and refreshed all repositories, but it still won't give the needed ones. What is it I'm doing wrong? Bear in mind that this is the first time I am online with Synaptic....

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=GrootBrak]I tried now to install smeg with the command:

sudo apt-get install smeg

The following errors jumps up.

> 
The following packages have unmet dependencies:
  smeg: Depends: python (>= 2.4) but 2.3.4-1ubuntu1 is to be installed
        Depends: python2.4-gtk2 (>= 2.6) but it is not installable
        Depends: python2.4-libxml2 (>= 2.6.17) but it is not installable
        Depends: python-xdg (>= 0.14) but 0.8-1 is to be installed
        Depends: python2.4-glade2 (>= 2.6) but it is not installable
E: Broken packages
[QUOTE]

Why does it gives me this? I have activated and refreshed all repositories, but it still won't give the needed ones. What is it I'm doing wrong? Bear in mind that this is the first time I am online with Synaptic....


Hmmm.....are you in Warty? Smeg depends on stuff in Hoary.

---

### Post by GrootBrak on 2005-07-21
Yeah. What is the link I should add to my repo's to upgrade? That is to say if its not a 500M download! My GPRS gives me about 32kb/s at a push. I have very few links in my repo's, about six I would say. My Debian CD's usually have most of the extra stuff. In fact it have tons of software not listed by Ubuntu.

---

