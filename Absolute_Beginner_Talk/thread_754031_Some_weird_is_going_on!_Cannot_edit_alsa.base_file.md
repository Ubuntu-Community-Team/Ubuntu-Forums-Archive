---
title: "Some weird is going on! Cannot edit alsa.base file!"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by javatyger on 2008-04-13
Hi guys.

Ok, this is weird. I was trying to edit the etc/modprobe.d/alsa-base so that I could get my sound to work, and each time I enter the code

"gksu gedit etc/modprobe.d/alsa-base" into the terminal, it keeps opening up home/username/etc/modprobe.d/alsa-base which does not exist. It's just getting really weird.

How can I edit the proper file????

---

### Post by lswest on 2008-04-13
you need to add a "/" before etc/ so that it reads /etc/.  Otherwise it looks for it within the home folder.

---

