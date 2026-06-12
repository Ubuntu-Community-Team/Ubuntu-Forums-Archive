---
title: "PowerBook G4 1.67 AirPort Problem"
date: 2008-11-23
forum: Apple Hardware Users
---

### Post by E-Rackattack on 2008-11-23
I'm Using a 17-inch PowerBook G4 1.67 GHz Running Mac OS X 10.3.9, OpenSUSE 11.0 (KDE 4.0) and Xubuntu 7.10 (Gutsy) using an AirPort Extreme card.

I know for a fact that these cards are Broadcom 43xx. I've managed to install the firmware on SUSE, but cannot figure out how to do so on Xubuntu. Is there a package I need to access via terminal?

Please help. I'd be incredibly happy for cooperation.

---

### Post by stream303 on 2008-11-23
This might do it for you:

[https://wiki.ubuntu.com/PowerPCFAQ#Will%20my%20wireless%20work?](https://wiki.ubuntu.com/PowerPCFAQ#Will%20my%20wireless%20work?)

---

### Post by E-Rackattack on 2008-11-23
It didn't work for me, sadly. I've tried connecting to the internet, too. Either way, Terminal gives me this:

**eric@PantherSUSE-XL:~$ sudo aptitude install bcm43xx-fwcutter**
[sudo] password for eric:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**Couldn't find any package whose name or description matched "bcm43xx-fwcutter"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

Am I doing something wrong?

---

### Post by Neostar on 2008-11-23
Have you tried the newer versions of Xubuntu.

---

### Post by E-Rackattack on 2008-11-23
I've tried newer versions. But the live CD acts wacky and never loads the splash screen or Xfce, period. I'd like help on this distro and version.

---

### Post by ntyhurst on 2008-11-23
i'm having the same problem.  i'm on a G4 ibook.  i have run and installed everything that has been suggested and i am still not detecting any of the wireless networks around here.  please, help.

---

