---
title: "(almost) Fresh install."
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by xdarkday on 2007-12-19
Is there a way to keep all of my saved files but go back to a fresh install of ubuntu. I am a newb and installed/unistalled things and I just want to go back to a vanilla ubuntu. I have some files I would love to keep, so really I just want to replace the desktop, and the core files.

Help :)

---

### Post by jken146 on 2007-12-19
The best advice when reinstalling an OS is: back up your personal files first!  Put them on CDs, DVDs, flash drives, another PC, whatever -- as long as you back up your files are safe.

When installing, I find that it helps to create an extra partition for /home.  That way I can reinstall whenever I want without worrying about my precious files (this is not a substitute for backing up, but it does make reinstalling the OS a lot easier).

---

### Post by bobplano on 2007-12-19
you could reinstall ubuntu, reformatting only the root partition, if you have a seperate /home partition. then just mark that /home partition as the /home one without reformatting. reformatting the "/" partition will get rid of any programs you have installed. if you don't have a seperate /home partition you need to back up the files you want.

Edit: I forgot how quickly these forums go :)

---

### Post by xdarkday on 2007-12-19
Is there and easy way to just hit "system defaults"?

---

### Post by jken146 on 2007-12-19
Not that I'm aware of.  The easiest way is a reinstall, or it would be for me.

If you have programs installed that you don't want any more, you can easily uninstall them.

---

### Post by xdarkday on 2007-12-19
well its because I get this error when I try to update

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and for some reason the otherday my theme got swtiched to another one and it gave me this error when I try to go back to human(custom)

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

---

### Post by Joeb454 on 2007-12-19
Sounds like you need to reinstall, it's the easiest option anyway :)

Like everybody said...back up your /home folder. And then when you reinstall, make a separate partition for /home.

Are you dual-booting or anything?

If not the alternate installer makes it quite easy to partition /home separately...plus it's quicker, you don't have to load the desktop :p

---

### Post by Hospadar on 2007-12-19
did you try running "sudo dpkg --configure -a"?  I bet it would fix your installation problem.

---

