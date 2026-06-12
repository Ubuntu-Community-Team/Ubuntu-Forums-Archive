---
title: "How do I change the default ALSA sound volume?"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by blasedeviant on 2006-12-04
It's far too loud for me, and I couldn't find the ALSA manpages.

And while I'm at it, how do I login as root on Ubuntu Edgy so I don't have to use sudo every time? It never prompted me for a root pass during install, and logging in with no password doesn't work...

---

### Post by Sef on 2006-12-04
> And while I'm at it, how do I login as root on Ubuntu Edgy so I don't have to use sudo every time? It never prompted me for a root pass during install, and logging in with no password doesn't work...


Sudo is temporary root.  Root is disbled by default because it is safer.  Read [RootSudo]("https://help.ubuntu.com/community/RootSudo") for more info.

---

### Post by yabbadabbadont on 2006-12-04
Try running "sudo alsamixer", then to save the settings, "sudo alsactl store" to save them.  There is no root user in Ubuntu, sudo is used instead.  You can get a similar effect by running "sudo -s -H" which will keep you at a root prompt until you exit that terminal/console session.

---

