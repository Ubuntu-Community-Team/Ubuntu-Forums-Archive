---
title: "uninstall beryl???"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-10-17
I installed beryl and emerald a couple of weeks ago and found it a bit buggy, I have not used it for awhile and want uninstall it, does anyone know if there is a how-to on uninstalling?  When I originally installed I made a copy of my orig. Xorg.conf, downloaded the things needed and put 2 lines in my sessions/startup programs.

I'm at school right now and can't check my sys. but please tell me there is an uninstall script somewhere in my puter...

---

### Post by thephotoman on 2006-10-17
Replace the current versions of the configuration files with the backups.  Then, change into the directory for the Beryl sources and type "sudo make uninstall", if you installed Beryl from the sources.  If you installed them from the repositories, a simple "sudo apt-get remove beryl" should do the trick.

---

### Post by marx2k on 2006-11-03
which config files are affected by Beryl?

I also would like to uninstall Beryl but am not sure what config files were altered

---

