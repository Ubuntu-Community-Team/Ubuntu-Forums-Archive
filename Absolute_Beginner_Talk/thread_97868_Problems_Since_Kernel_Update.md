---
title: "Problems Since Kernel Update"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Weta on 2005-12-01
Hello 

I installed the latest kernel updates recently (using Smart Upgrades), but now my modem doesn't work.  During boot I get the following messsage: "Trying to automatically build the driver modules. Please ensure that the kernel-headers or kernel-source package is installed.  On Debian try "apt-get install kernel-headers-2.6.10-6-386", and 'Warning Missing File: /usr/src/linux/autoconf.h"

I cannot find the header file 2.6.10-6-386 on my file system.  There is however a "autoconf.h" file in the /usr/src/linux-headers-2.6.10-5-386/include/linux folder.

The update process u[graded linux-386, linux-image-386 and linux-restricted-modules-386, and installed linux-image-2.6.10-6-386 and linux-restricted-modules-2.6.10-6-386.

It looks to me as though the update process did not include the updated header file.  Can someone confirm whether this is correct please.  If so, then how can I install the file (remember, I cannot access the Internet - and I am a beginner).

[The modem is an internal software modem, based on the Linuxant comercial software, and worked fine until after I shut down after the updates were installed]

Thank you


Weta

---

### Post by WebPhut on 2005-12-01
I'm having a similar problem.  Installed with 386 kernel and wifi addapter worked automagically.  Used synaptic to upgrade kernel to 686.  It boots up fine, but wifi is nowhere to be seen.  Where did my driver go and how do I get it back? Luckily, I can still boot the old 386 kernel and ask for help.

---

