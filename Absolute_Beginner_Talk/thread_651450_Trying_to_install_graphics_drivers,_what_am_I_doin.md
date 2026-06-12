---
title: "Trying to install graphics drivers, what am I doing wrong?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by SpaceBandito on 2007-12-27
I'm new to Ubuntu and Linux in general and seem to have run into a problem; I can't install the drivers for my video card (ATI x1900xtx).

I keep getting the "must log in as a super-user" message even though I've been prefacing my install commands with 'sudo'

Here's what I've been doing:

duncan@gaming-alt:~/Desktop$ sudo chmod +x ati-driver-installer-8.443.1-x86.x86_64.run
[sudo] password for duncan:
duncan@gaming-alt:~/Desktop$ ./ati-driver-installer-8.443.1-x86.x86_64.run
Created directory fglrx-install.Zy6012
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.443.1.........................................................................
.............................................................................................................................................................
.............................................................................................................................................................
.............................................................................................................................................................
.......................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.1 and later releases 64-bit
Removing temporary directory: fglrx-install.Zy6012

Am I doing anything wrong? Why won't it install?

---

### Post by Perfect Storm on 2007-12-27
Everytime you're going to affect something other than your home, you need to use sudo, in this case;

```
sudo ./ati-driver-installer-8.443.1-x86.x86_64.run
```


By the way - Have you tried the ATI driver that's with Ubuntu (restricted driver)?

---

### Post by logos34 on 2007-12-27
try 

**[B]sudo ./**ati-driver-installer-8.443.1-x86.x86_64.run[/B]

Kill X server first and drop to the console prompt before you run above command:

ctrl+alt+F1

sudo /etc/init.d/gdm stop

---

### Post by spiderbatdad on 2007-12-27
is there a readme or install file in the directory, or from the site where you got the driver. There are sometimes kernel requirements prior to being able to install drivers if they are from source code.

---

### Post by Casual Fan on 2007-12-27
Yeah, like A.I. said, hell of a lot easier to just let Ubuntu install your driver instead of downloading a package and trying to install it. You should be able to run Compiz etc. just fine with the restricted driver in the repos.

---

### Post by SpaceBandito on 2007-12-27
Wow. Thanks for all the quick replies. 

I've not tried the default drivers, but since I got the official drivers working, I guess I'll just use them until I run into any problems.

---

### Post by Afkpuz on 2007-12-27
You can also install your driver by going to System>Administration>Restricted Drivers Manager

Check the box next to your video card and it will install for you.  Afterwards, you'll need to restart your computer.

---

