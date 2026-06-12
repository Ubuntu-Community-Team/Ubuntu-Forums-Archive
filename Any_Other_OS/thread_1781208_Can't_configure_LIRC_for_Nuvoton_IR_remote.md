---
title: "Can't configure LIRC for Nuvoton IR remote"
date: 2011-06-13
forum: Any Other OS
---

### Post by HydroDiOxide on 2011-06-13
I've got an Asrock ION 330 HT set up as an HTPC with Maverick (Linux Mint edition). I've recently replace my 2.6.35-22 kernel with the 2.6.35-28 kernel. After this my remote wasn't working anymore so I figured I had to reinstall the remote driver. I downloaded the driver from the [Asrock site]("http://www.asrock.com/Nettop/download.asp?Model=ION%20330HT&o=Linux"), the 2.6.35-22 version. There wasn't a precompiled driver so I used the source provided with the 2.6.35-22 package to compile it against the newer kernel (roughly following [this instruction]("http://kerkhove.net/glob/41/2010-07-03/getting-the-lirc_nct677-module-to-work-on-ion330-with-ubuntu-kernel-2-6-32-23.html")). This after removing all the old stuff and reistalling Lirc and the Lirc-sources package.

Everything seems to compile and install ok. When I do an lsmod I can see the module loaded (lirc_wb677). However, Lirc can't be configured to use the driver. After compiling and installing everything I run a dpkg-reconfigure on lirc. I would expect that I could also choose the Nuvoton driver in the ncurses interface, but this is not the case. The result is that the irexec service isn't able to start, rendering my remote unusable.

Anyone any idea on how to get the Nuvoton driver available in the lirc configuration? Me thinks that I did everyting I had to.

---

### Post by Perfect Storm on 2011-06-13
Moved to Other OS/Distro Talk.

---

### Post by HydroDiOxide on 2011-06-16
bump

---

### Post by HydroDiOxide on 2011-06-17
Still no success on configuring lirc for the nuvoton Asrock remote; it just won't show up in the configuration menu. However, I tried to use the Microsoft Media Center configuration and it worked with the nuvoton remote as well.

---

