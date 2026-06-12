---
title: "Synaptic won't fully open, can't use superuser privileges"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by seaworthy4life on 2007-07-02
So I had to reinstall because of a Gnome bug.  After I have reinstalled, I was fixing up multimedia, adding new stuff this way, which I had no problem with the first time:

sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

Then, I tried to access Synaptic afterwards and I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So I try to run 'dpkg --configure -a', and no matter how I try to use su, it tells me that authentication failed, like the password is not working or something, though I think it is because of another reason.  Synaptic is not running.  The password is right.  I rebooted.  I don't know what to make of it.

---

### Post by Seisen on 2007-07-02
Try** "sudo" **instead of **"su"**

---

