---
title: "error running ati driver installer"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by plursh on 2007-04-08
ive been following one of the walk-throughs on the community ubuntu documentation ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28binary%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28binary%29) to be exact) and it said to do these commands:

sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh

when i did them i kept getting an error:

root@ubuntu:~# sudo ln -sf dash /bin/sh
root@ubuntu:~# bash /home/bryan/ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/edgy
Created directory fglrx-install.ss4418
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.35.5.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: 178: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.ss4418

amd athlon 64 3200+
radeon x800gt

thanks in advance to anyone who replies

---

### Post by bwhite82 on 2007-04-09
I think you may have downloaded the wrong driver for your architecture. Try [this page]("http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871,00.html").

EDIT: That page only shows drivers for your CPU, disregard. Hmmm, it's complaining about your architecture. Someone with more experience than I can probably help you out on this one.

---

### Post by freebird54 on 2007-04-09
If I read this correctly - you might not need the driver for your mode of card.  Here's a quote from the link you showed:

```
Note that if you own an ATI card from the R400 series or below, you already have working 2D and may have accelerated 3D with the default drivers. These cards include:

    *

      **R400 series Xnnn (X800, X700, etc) (3D works)**
    *

      R300 series (9300+) (3D works)
    *

      R200 and R100 series (9200 and below)

```

COuld be the source of the difficulty.  Can you determine the chipset your card uses?

---

