---
title: "Mint 13: Additional Drivers Fails to Install Nvidia, Breaks X"
date: 2012-06-15
forum: Any Other OS
---

### Post by buzzingrobot on 2012-06-15
Posting this here because I'm not getting a response on the Mint boards:

I've done an install of Linus Mint 13, the MATE version. "Additional Drivers" is failing, repeatedly, to install the proprietary Nvidia driver.

This is surprising because it is, presumably, the same code used on Ubuntu, which works flawlessly for me. Mint has even bothered to removed references to Unity.

Additional Drivers reports the driver was installed.  I reboot to a shell and the warning that "Failed to start the X server...."

I've tried nvidia.xconfig, but it was not installed.   Aptitude shows "nvidia-common", "nvidia-settings" and "nvidia-current-updates" are installed.  However, the original xorg,conf has not been edited to reflect the nvidia installation.  I've tried to run nvidia-xconfig but it has not been installed.

I've tried purging all the nvidia packages, and re-installing from apt-get.  That generates error messages about broken packages and unresolvable dependencies.

To complicate things, I can't boot with this Nvidia card and any 3.2/3.3 kernel with Nouveau.  It crashes as soon as Nouveau starts to load. Even a LIveCD.  So, I need to use kernel boot options until I get an Nvidia driver installed.

---

### Post by Dlambert on 2012-06-15
Maybe try the cinnamon install? It could just be MATE on your system.

---

