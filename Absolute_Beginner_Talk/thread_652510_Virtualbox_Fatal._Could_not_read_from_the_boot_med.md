---
title: "Virtualbox: Fatal. Could not read from the boot medium. System halted."
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by S3loth on 2007-12-28
I'm trying to run VirtualBox to use vista from my harddrive. Does this mean that it will open vista if I have it dual booted with Ubuntu? I keep getting the error Fatal. Could not read from the boot medium. System halted. every time I try to boot from the hard drive.

---

### Post by bump_ on 2007-12-28
No, as far as I know, you will have to install a new copy of Vista under virtualbox. It will not use the dual boot copy on your hard drive. 

If you are running Virtualbox for the first time and getting that error, that means you have not yet installed Vista under VB. Start the virtual machine you made for Vista and pause it when it says "Innotek". 

The next step differs based on how you will install Vista. If you have the actual installation disk, pop it in and go to "Devices ->  Mount CD/DVD-ROM" and click on your cd drive.

If you are installing from an image of the installation disk, go to "Devices -> Mount CD/DVD-ROM -> Mount CD/DVD-ROM Image" and click on the image of the installation disk you are using.

---

