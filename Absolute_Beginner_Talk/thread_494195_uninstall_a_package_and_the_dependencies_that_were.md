---
title: "uninstall a package and the dependencies that were installed"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by mr.v. on 2007-07-06
Hi all--

basically I installed a package that installed a bunch of other packages, and I want to remove all of them at once based on the original package...can this be done?

Here's the longer version of the story...

I've pretty much used synaptic to install the few packages I needed. However, I needed to compile a program from scratch and it had libqt as a requirement. So I installed libqt4-core and libqt4-gui...however, it obviously also needed the headers/developement libraries. So I installed 
libqt4-dev

However, libqt4-dev installed ~40 additional packages. I'd like to remove libqt4-dev after I compile the program.

Then it turned out I also needed the qmake from qt3-apps-dev since it wouldn't compile with the qt4 qmake...which installed another 30 packages.

uyyyyy...so now I want to remove the qt3/4 dev packages and ALL the dependencies that it installed along side it. Is this possible? Neither Mark for Removal nor Mark for Complete Removal of qt4-dev or qt3-apps-dev in synaptic led to removal of the 70 other packages that were installed along with the qt dev packages.

How can I remove all of those other ones too?!
Thanks for the help!

---

### Post by r4ik on 2007-07-06
Try,

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

Good luck !

---

