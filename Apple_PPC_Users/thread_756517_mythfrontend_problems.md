---
title: "mythfrontend problems"
date: 2008-04-15
forum: Apple PPC Users
---

### Post by sheetzam on 2008-04-15
Trying to install mythfrontend on a 400mhz ibook.  Tried it on Ubuntu 7.10 and Xubuntu 7.10, both with the same results.  The version of mythtv-frontend installed is 0.20.2-0ubuntu10.1.
Whenever I start mythfrontend, I get an immediate Illegal instruction (core dumped).
Any ideas?

---

### Post by kingmoffa on 2008-04-16
You could try compiling from source , i tried that a year ago on PPC and didn't get anywhere. However it may well compile now.

remove all your myth stuff using synaptic.

Then follow this:

[http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy](http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy)

400mhz is pretty slow. But may work. I did have mythfrontend working on a PII 350 , and it works on my 600mhz eeePC. If its a G4 , there is some altivec compile options you can use to help.

---

