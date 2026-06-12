---
title: "Upgrade to 7.10 Trashed?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by yerdon on 2007-11-08
Hi,

Yesterday I upgraded my 7.04 system to 7.10.  Everything was pretty easy and I just followed the prompts all the way through.  I restarted the system, logged on and I get a GRAY-BLUE SCREEN.  

I can move the mouse around and the keyboard isn't locked.  If I press Ctrl+Alt+F1 it takes me to a command-prompt.  I log in and was able to restart the GDM.  But after I log in it does the same thing.

I'm pretty new to Linux.  Any thoughts on what might be wrong?

Thank you!

Joseph

---

### Post by reckless2k2 on 2007-11-08
i'm pretty sure it's the video driver you are using. did you have a proprietary ati or nvidia driver in 7.04?

a quick edit in xorg.conf should fix you or reinstall the nvidia driver if that's the case.

---

### Post by yerdon on 2007-11-08
Yes, I am using an NVIDIA driver.  I tried re-installing it from the command line.  Everything starts to work like when I originally installed the driver, but then I get to these prompts:

ERROR: The runtime configuration check failed for the library 
'libnvidia-tls.sl.100.14.19' (Expected: 
'/usr/lib/tls/libnvidia-tls.so.1', found: 
'/usr/lib/libnvidia-tls.so.1').  The most likely reason for this is 
that conflicting OpenGL libraries are installed in a location not 
inspected by 'nvidia-installer'.  Please be sure you have uninstalled 
any third-party OpenGL and/or third-party graphics driver packages.

and then:

ERROR: Installation has failed.  Please see the file 
'/var/log/nvidia-installer.log' for detils.  ...

How can I determine any conflicting OpenGL or draphics drivers I might have?

Thank you!

Joseph

---

### Post by skyjacker on 2007-11-08
> **yerdon said:**
> Yes, I am using an NVIDIA driver.  I tried re-installing it from the command line.  Everything starts to work like when I originally installed the driver, but then I get to these prompts:

ERROR: The runtime configuration check failed for the library 
'libnvidia-tls.sl.100.14.19' (Expected: 
'/usr/lib/tls/libnvidia-tls.so.1', found: 
'/usr/lib/libnvidia-tls.so.1').  The most likely reason for this is 
that conflicting OpenGL libraries are installed in a location not 
inspected by 'nvidia-installer'.  Please be sure you have uninstalled 
any third-party OpenGL and/or third-party graphics driver packages.

and then:

ERROR: Installation has failed.  Please see the file 
'/var/log/nvidia-installer.log' for detils.  ...

How can I determine any conflicting OpenGL or draphics drivers I might have?

Thank you!

Joseph If you had "Envy" installed in 7.04, you needed to un-install it prior to upgrading to 7.10 (per instructions on Envy website). That might be what is causing your problems. I did a "clean install to 7.10, and had no problems. I also had "Envy" installed in 7.04.

---

