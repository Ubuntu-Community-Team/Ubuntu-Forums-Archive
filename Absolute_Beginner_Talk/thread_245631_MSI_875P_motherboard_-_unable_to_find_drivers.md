---
title: "MSI 875P motherboard - unable to find drivers"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by PBoz on 2006-08-28
Please forgive my lack of familiarity with Ubuntu.  I downloaded and installed 6.06 on a machine with an MSI 875 P motherboard.  Just spent 2 days trying to find out where to get the drivers for this chipset (intel 875).  It seems to recognize my ATI Raedon 9800 pro, but I appear to need a combination of drivers for the Intel chipset, and the 9800 pro, in order to enable me to turn on the graphics acceleration and use a screen resolution greater than 1280x1024.  I tried everything I could find in the Synaptic installer yesterday, but nothing seems to work.   Anyone out there able to point me in the right direction?

---

### Post by rbmorse on 2006-08-28
I run the same combination. 

You don't need chipset drivers for the 875P/ICH5...it's fully supported by the linux kernel....except for the Intelmatrix RAID - that one I'm not sure about as I don't use it. 

The driver package for the Radeon 9800 Pro is FGLRX. It's in one of the repositories.  Make sure you have the kernel sources and restricted  modules for your kernel version installed, then you can install it with synaptic, aptitude or apt-get as you desire. Do a search on FGLRX to get all the gory details.

---

