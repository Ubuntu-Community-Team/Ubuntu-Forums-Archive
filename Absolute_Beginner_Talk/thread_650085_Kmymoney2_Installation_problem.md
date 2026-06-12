---
title: "Kmymoney2 Installation problem"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by scyowner on 2007-12-25
I am new to Ubuntu. In looking around a little, I like what I see. I needed a program to replace Quicken and KMymoney seems to be a good replacement. However I can't seem to get it installed.

When I try to install from Add/Remove Applications, I get an error stating that there are conflicts and to use Synaptic Package Manager. When I try to install from there, I get the following error:

kmymoney2:
 Depends: kdelibs4c2a (>=4:3.5.7-1) but it is not installable
 Depends: libaudio2  but it is not installable
 Depends: libofx3 but it is not going to be installed
 Depends: libosp5 (>=1.5.2-1) but it is not installable
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable

How do I get this program to install?

Any help from the community would be greatly appreciated!!!

---

### Post by frank002 on 2007-12-25
I know this is not the answer you are looking for but why not try gnucash? I have been using gnucash as a replacement for Quicken for about 2 months. It takes a little getting used to but works just fine.

---

### Post by frank002 on 2007-12-25
You need to open Synaptic and search for those dependencies. 
 Open Synaptic and click search. Then type libaudio2. Check it for installation. Do the same for the others. Once you have installed the dependencies,  install KMymoney. That should work.

---

### Post by oygle on 2008-02-02
I had the same problem around early Nov, and then I installed 7.10, and after the first lot of updates, installed KMyMoney okay.

Does it install okay now ?

---

