---
title: "Google earth on Ubuntu 6.06 with i810"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by abarth on 2007-05-18
Hi all,
I installed google earth from google's website. Installation seems to be successfull, but if I launch the program, google earth starts with the slash screen and then hangs (until I kill it after 5min). 

I have Intel 915 with the i810 driver:

Any help is very appreciated. 
Thanks
Alex

lspci:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
[...]

---

### Post by n8bounds on 2007-05-18
uninstall it, add the medibuntu repos, and install their version with aptitude

check these guys out:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

then you can sudo aptitude update and sudo aptitude install googleearth

---

