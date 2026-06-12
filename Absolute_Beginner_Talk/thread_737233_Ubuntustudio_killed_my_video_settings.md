---
title: "Ubuntustudio killed my video settings"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by apokkalyps on 2008-03-27
I tried to install the ubuntustudio packages and they installed fine and said I needed to reboot.  I didn't reboot right away, and all my video settings were fine.  I also installed Linux Multimedia Studio, after installing Ubuntustudio, but its mostly a sound package so it seems less likely the culprit.  By the way I installed all 3 ubuntustudio packages (images, video, and sound).  After rebooting, my video settings all got hosed.  My resolution is small, and my compiz settings seem to be gone.  Is there any way to get  back?  

Also I thought about uninstalling Ubuntustudio, but I don't think I could if I wanted to, because as it turns out, its just a collection of other packages that get dumped onto your computer, so the majority of the install is dependancies and I would have no idea which of them to uninstall.  (I'm a little irritated by this, since I was expecting one big application, not to have my "Sound & Video" menu flooded with 20 little apps.  But thats irrelevant to the question at hand.)  Can anyone suggest a process for getting my system back the way it was yesterday?  I'm afraid to even open ccsm or raise my resolution back because it might overwrite my config files with default values or something.

Please help, thanks.

---

### Post by apokkalyps on 2008-03-28
Ok, so from searching around a few other people have had this problem.  It seems to happen on 64 bit using the restricted nvidia drivers.  ubuntustudio-audio i think it is, somehow screws up the linux-restricted-modules package(s).  Uninstalling them and reinstalling them did nothing.  I'm trying use the Envy scripts to uninstall and reinstall the drivers.

---

