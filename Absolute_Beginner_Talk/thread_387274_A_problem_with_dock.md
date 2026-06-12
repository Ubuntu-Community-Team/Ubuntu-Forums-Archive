---
title: "A problem with dock"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-03-18
When i try to install kiba-dock, i get this problem:

ajeffreys@ajeffreys-laptop:~$ cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cvs checkout: CVS password file /home/ajeffreys/.cvspass does not exist - creating a new file
cvs server: cannot find module `kiba-dock' - ignored
cvs [checkout aborted]: cannot expand modules
ajeffreys@ajeffreys-laptop:~$ 


Please help. I am following this tutorial: [http://www.abitofcode.org/2007/01/05/installing-kiba-dock-on-ubuntu-edgydapper.html]("http://www.abitofcode.org/2007/01/05/installing-kiba-dock-on-ubuntu-edgydapper.html")


Thanks,

Ajeffreys

---

### Post by louis_nichols on 2007-03-18
The error means that kiba-dock is no longer in the cvs tree from the tutorial. You should look for a more recent and up-to-date tutorial. Or, keep using that one, but find the actual cvs repo where they keep kiba-dock now.

---

