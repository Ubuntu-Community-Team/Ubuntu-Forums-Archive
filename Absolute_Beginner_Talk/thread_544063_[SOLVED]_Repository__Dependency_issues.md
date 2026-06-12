---
title: "[SOLVED] Repository / Dependency issues"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-09-05
I used this guide, trying to get some additional plugins for compiz.  

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

In retrospect, stupid.  

Now I'm having dependency issues, I cannot purge compiz, cause it is dependent on compiz-extra.

I'm caught in a loop of dependencies and cannot get out :(

" sudo apt-get -f install "


bo@bo-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  compiz: Depends: compiz-fusion-plugins-main (>= 0.5.2+git20070829) but it is not installable
          Depends: compiz-fusion-plugins-extra (>= 0.5.2+git20070829) but it is not installable
  compiz-core: Breaks: compiz-extra (<= 0.3.6.1-0ubuntu2) but 0.3.6.1-0ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by SOULRiDER on 2007-09-05
Do a ```
sudo aptitude update
sudo aptitude dist-upgrade
``` and see how it goes.

---

### Post by lmlypfan on 2007-09-05
Awsome.

Now I need to figure out how to repair compiz. 

Thanks again

---

