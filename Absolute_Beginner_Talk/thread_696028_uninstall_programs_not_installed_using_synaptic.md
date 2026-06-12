---
title: "uninstall programs not installed using synaptic"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by pmsagdeo on 2008-02-13
I installed freeCAD using the .deb package.  I would like to remove it.  I cannot use the add/remove software because it does not find it.  Please advise on how to remove it.  Thank you.

---

### Post by mmb1 on 2008-02-13
try to install it again, and a prompt should show up with some options, then select to uninstall.

---

### Post by kellemes on 2008-02-13
> **pmsagdeo said:**
> I installed freeCAD using the .deb package.  I would like to remove it.  I cannot use the add/remove software because it does not find it.  Please advise on how to remove it.  Thank you.

Use synaptic, apt-get or aptitude.
"gksudo synaptic"
"sudo apt-get remove freeCAD"
"sudo aptitude remove freeCAD"

Edit: use "apt-cache search" to find out the name of the package.

---

### Post by piousp on 2008-02-13
Ha ha ha! I've always asked the same thing. So far, i think you can try the "aptitude" command.

---

