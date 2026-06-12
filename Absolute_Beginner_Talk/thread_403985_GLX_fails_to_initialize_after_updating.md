---
title: "GLX fails to initialize after updating"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by UpperNinety89 on 2007-04-07
Last night I applied a whole bunch of upgrades after installing Ubuntu 6.10 Edgy Eft onto a new partition. After rebooting, everything SEEMED to be ok but when I went into the Screensavers preferences to see if the 3D ones increased performance after the update, but I found that they didn't even show anymore. Upon viewing the Xorg.0.log in the /var/log directory, I found this:

...
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
error opening security policy file /usr/lib/xserver/SecurityPolicy
...

Just a little information about what I have on my system. I'm running a GeForce 6200SE TurboCharge card and looking at the Synaptic Package Manager I am running version 1.0.8776+2.6.17.7 of the NVIDIA binary XFree86 4.x/X. Org driver.

Any assistance would be greatly appreciated.

---

### Post by Bachstelze on 2007-04-07
Make sure you have the restricted-modules matcfhing your new kernel :

```
sudo aptitude install linux-restricted-modules-$(uname -r)
```

---

### Post by UpperNinety89 on 2007-04-07
If you could explain exactly what that does it'd be a big help to me. I just did that in Terminal and as far as I can tell nothing changed. Here's the output in the console window:

user@user-desktop:~$ sudo aptitude install linux-restricted-modules-$(uname -r)
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Bachstelze on 2007-04-07
It wil install the nvidia kernel module which is a part of the driver you're apparently missing. Make sure you don't have any software managament app opened before running that commend like Synaptic for example.

---

### Post by UpperNinety89 on 2007-04-07
user@user-desktop:~$ sudo aptitude install linux-restricted-modules-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Thats what I got this time, give me a second to see if anything was fixed.

---

### Post by UpperNinety89 on 2007-04-07
Nothing changed, I'm still getting the same error in the Xorg.0.log

---

