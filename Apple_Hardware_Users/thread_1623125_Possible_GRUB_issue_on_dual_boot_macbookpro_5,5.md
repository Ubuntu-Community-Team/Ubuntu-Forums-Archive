---
title: "Possible GRUB issue on dual boot macbookpro 5,5"
date: 2010-11-16
forum: Apple Hardware Users
---

### Post by RBM on 2010-11-16
Last night I installed ubuntu 10.10 unto a macbook pro 5,5 following the instruction from the MactelSupportTeamAppleIntelInstallation however I made a mistake during the installation process.  I forgot to go into advance settings and choose to install the bootloader on /dev/sda3. I'm not exactly sure why this step was needed since everything was working fine anyways, but I was wondering how can I remove the bootloader from /dev/sda and install it on /dev/sda3 without breaking anything. 

Reference: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu)

---

### Post by Zookalicious on 2010-11-24
Are you still able to boot into Mac OS X? If you can still boot into both OS's, I wouldn't worry about it too much.

edit: Writing the bootloader to /dev/sda overwrites the normal Apple EFI partition I believe. So if you start experiencing errors on the Apple partition then this is something to look into.

---

### Post by rafamundez on 2011-01-30
I did the same thing...except i couldn't find the "advanced" button; not so much that I forgot about it.


Also, hows does the 64 bit version run on the macbook pro 5,5?


And is there any slightly more comprehensive guide to dual booting Mac OS X and Ubuntu 10.10?  I had to delete everything and am going to restart from scratch so I wanted to be more confident in everything I'm doing...

Thanks!!!!

---

