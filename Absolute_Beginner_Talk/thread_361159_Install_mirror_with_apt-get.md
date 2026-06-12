---
title: "Install mirror with apt-get"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by VertigoRay on 2007-02-14
Using apt-get, how do I install the mirror executable?  I've already uncommented the univesal sections of the sources.list, but my apt-cache still is not finding a search for mirror.  Maybe I just do not know what I'm searching for?

Basically, running Ubuntu 6.10 Server and I want to set up a mirror.  I cannot do this because the mirror command is not recognized.

Any assistance with this matter would be appreciated.

---

### Post by aysiu on 2007-02-14
After you make changes to your sources.list, you have to *update* before you can *install*: ```
sudo apt-get update
sudo apt-get install mirror
``` The *update* part of the *apt-get* command checks to see what packages are currently available in the repositories.

---

### Post by VertigoRay on 2007-02-14
Worked great.  Thank you.

---

