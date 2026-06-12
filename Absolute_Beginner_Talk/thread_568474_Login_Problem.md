---
title: "Login Problem"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Astrodan on 2007-10-05
I can only login using the Terminal screen.  When I try to get in using GNOME, I get a message:

GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator.  

I've tried deleting some files and tried to apt-get install a new GNOME.  I'm  hoping I can be restored some way.  Thanks in advance,

Dan

---

### Post by HermanAB on 2007-10-05
Hmm, I suggest that you make a new user account and copy your private data over.  That is usually the easiest way to fix a messed up desktop system, since it only takes a few seconds.

Cheers,

Herman

---

### Post by AlexenderReez on 2007-10-05
maybe you have install software that exceed your limit space.....try to remove all unnecessary installer with ...> sudo apt-get autoclean

if still failed....remove the last software you installed before you reboot....

---

