---
title: "A few questions"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by MadsRH on 2007-03-11
1:
I need help reinstalling conky! Didn't have universe repo enabled and when I boot the desktop hasn't changed. I followed this guide: [http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)
Does anyone know why nothing happens?

2:
I would like a 3d desktop (*xgl,compiz, looking glass or beryl*), just something very very easy to install. For an easy way I though I'd just update to Feisty Fawn, witch brings me to number 3

3:
Updating doesn't work. I get:
[B]An error occured
The following details are provided:
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)[/B]

Trying to update to Feisty using this command:  **gksu "update-manager -c -d"**
I get: **Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Underprocessen bzip2 returned an errorcode (2)**

Any help at all is welcome! Thank you...
**MadsRH**

---

### Post by igknighted on 2007-03-11
> **MadsRH said:**
> 1:
I need help reinstalling conky! Didn't have universe repo enabled and when I boot the desktop hasn't changed. I followed this guide: [http://www.ubuntuforums.org/showthread.php?t=205865](http://www.ubuntuforums.org/showthread.php?t=205865)
Does anyone know why nothing happens?

2:
I would like a 3d desktop (*xgl,compiz, looking glass or beryl*), just something very very easy to install. For an easy way I though I'd just update to Feisty Fawn, witch brings me to number 3

3:
Updating doesn't work. I get:
[B]An error occured
The following details are provided:
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)[/B]

Trying to update to Feisty using this command:  **gksu "update-manager -c -d"**
I get: **Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Underprocessen bzip2 returned an errorcode (2)**

Any help at all is welcome! Thank you...
**MadsRH**

Well, as far as updating you have a dublicate line in your sources.list file.  Look through it until you find the offending line and delete it.  As far as your composite manager, fiesty has no real improvements in this category.  Go to [www.beryl-project.org](www.beryl-project.org), click on the wiki and look at the Ubuntu install instructions.  Fiesty is still an alpha, do not upgrade edgy to it yet unless you plan on using it for bug-testing only.  Daily updates will likely break things.

---

### Post by MadsRH on 2007-03-11
Thanks.
Maybe I just want to one that comes with an easy installation!

---

