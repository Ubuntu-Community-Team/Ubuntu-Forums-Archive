---
title: "3D effects in Linux on a MacBook"
date: 2007-09-08
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-09-08
After much experimentation and trial&error I have finally got my MacBook (2.16GHz, 1GB RAM, 945GM) set up to multiboot OSX together with Ubuntu Feisty, OpenSUSE 10.2 and Sidux 2007-3
However, I'm still having a problem with 3D effects. I can only get Compiz-Fusion fully functional in Sidux but not in either of the others. However, Beryl runs fine in Ubuntu but I can only get Compiz (not C-F) working in OpenSUSE.
I am convinced that the problem lies in the /etc/X11/xorg.conf files but I just can't get this right even following the working version of this file in Sidux.
Has anybody got any views on what needs to be done to persuade Compiz-Fusion to work on either Ubuntu Feisty or OpenSUSE in a MacBook?

---

### Post by benanzo on 2007-09-08
I've got a first-gen MacBook running Gutsy and CF works flawlessly with no tinkering.  All I had to do in Feisty was set up the repos and install.  I can't think of what problems you might be having, other than to say that if Beryl works, it's probably not your xorg.conf file.

---

### Post by PaulFXH on 2007-09-09
Yes, thank you.
I've got it working perfectly now in Ubuntu. The key for me was to get the /etc/X11/xorg.conf file right and to acknowledge that what works for nVidia may not (indeed probably won't) work for 945GM.[-X

---

