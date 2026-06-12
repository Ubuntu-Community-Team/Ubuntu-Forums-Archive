---
title: "make DVI primary monitor in DVI/VGA dual set up?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by ilovebsod on 2007-12-18
Found several posts asking this same question, but no real answer.

Just installed 7.10 on my primary rig that has a 6800GT.  Installed the Nvidia driver.  Tried Twinview and Ubuntu's built in Screens and Resolution config tool and nothing I do will make my DVI attached monitor the primary.  Using Ubuntu's config tool usually ends up in X running in "safe mode" until I reset the changes I made (i.e. checking the 'default' box for the DVI attached monitor).

any help?

Thanks!

---

### Post by CatKiller on 2007-12-19
> **ilovebsod said:**
> nothing I do will make my DVI attached monitor the primary.

I'm not entirely sure what you mean by this, but you can change placement info with the "ServerLayout" section of your /etc/X11/xorg.conf file, with the first Screen defined in that section being the one that the login window appears on. See **man xorg.conf** for more information.

---

