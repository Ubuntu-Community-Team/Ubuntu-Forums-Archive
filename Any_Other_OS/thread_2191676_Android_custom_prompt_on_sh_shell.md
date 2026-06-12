---
title: "Android custom prompt on sh shell"
date: 2013-12-03
forum: Any Other OS
---

### Post by zealibib slaughter on 2013-12-03
hello everyone I got a question and I hope someone may have an idea of where to look.  I am trying to set a custom prompt on my android (sh shell non login).  I have edited /etc/profile but this seems to be read only if its a login shell (sh -l).  I can't make a shell script to launch the shell as login every time because my android doesn't like for the sh binary to move.  Does anyone know what file gets read by bourne shell at start?

---

### Post by zealibib slaughter on 2013-12-03
Ok well I got a workaround (which is actually a better solution) but I would still like to know which files bourne shell reads at init. 

Here is my workaround
download bash for android from xda, push it to /system/bin, back up system/bin/sh, remove sh, make bash executable, ln -s sh to bash, make bash_profile, reboot. Now I have bash shell which is better than bourne shell so Im gonna mark this as solved but please If you know the answer to my original question post it here just in case I have to revert back to bourne shell at some time.

---

