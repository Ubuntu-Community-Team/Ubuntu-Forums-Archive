---
title: "ubuntu desktop package help"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by squiggs on 2007-11-30
Followed the Soundcard guide (trying to get it working) however please advise on what to do about the desktop removal options failing!!! Im scared to reboot at this stage incase I lose my desktop.



paul@paul-desktop:~$ sudo modprobe snd-emu10k1
[sudo] password for paul:
paul@paul-desktop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-sound-base is already the newest version.
Package alsa-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  linux-sound-base
E: Package alsa-base has no installation candidate
paul@paul-desktop:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alsa-base is not installed, so not removed
The following packages will be REMOVED
  alsa-utils* fast-user-switch-applet* gdm* linux-sound-base* ubuntu-desktop*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 20.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88893 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing fast-user-switch-applet ...
Purging configuration files for fast-user-switch-applet ...
Removing gdm ...
Purging configuration files for gdm ...
Removing user `gdm' ...
Done.
dpkg - warning: while removing gdm, directory `/usr/share/gdm/applications' not empty so not removed.
Removing alsa-utils ...
Purging configuration files for alsa-utils ...
Removing linux-sound-base ...
Purging configuration files for linux-sound-base ...
paul@paul-desktop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-sound-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-sound-base has no installation candidate
paul@paul-desktop:~$ sudo apt-get install gdm ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gdm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gdm has no installation candidate
paul@paul-desktop:~$

---

### Post by SunnyRabbiera on 2007-11-30
owie....

perhaps you can try to install another desktop enviroment, like KDE
try to install KDE via synaptic and see what happens.
I only suggest KDE as you can also install KDM that might resolve your GDM issue...
I really hope you can get a DE running, otherwise i have no suggestions

---

### Post by forestpixie on 2007-11-30
> Do you want to continue [Y/n]? y
(Reading database ... 88893 files and directories currently installed.)
Removing ubuntu-desktop ...

Is it this desktop you're worried about? 
Ubuntu-desktop is a meta package - basically if you remove something from within the 'package' you haven't got the same thing anymore and are in effect uninstalling it.

I removed the gnome openoffice - which removed ubuntu-desktop, someone else will be along I'm sure with their tuppence worth - but you should be fine

---

### Post by forestpixie on 2007-11-30
Missed that bit at the bottom - have you tried installing the desktop

```
sudo aptitude install ubuntu-desktop
```

to see what it says

---

### Post by squiggs on 2007-12-01
Unfortunately, Linux froze before I could read your messages last night. Im now back in Ubuntu from the Live CD. running said command results in this. Might be worth ammending the Sound card guide to note potential problem to be aware of and fixes. Such as desktop-packages being removed will result in a command prompt if you cant get them reinstalled.

ubuntu@ubuntu:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by nhandler on 2007-12-01
> **squiggs said:**
> Unfortunately, Linux froze before I could read your messages last night. Im now back in Ubuntu from the Live CD. running said command results in this. Might be worth ammending the Sound card guide to note potential problem to be aware of and fixes. Such as desktop-packages being removed will result in a command prompt if you cant get them reinstalled.

ubuntu@ubuntu:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

Before you run a command from the live cd, you need to chroot to your normal install of ubuntu. Otherwise, the commands are just being run for the live cd environment (where ubuntu-desktop is already installed). Look in the Hardy Development section of the forum. They have a stickied thread that explains how to chroot to your installed ubuntu.

Otherwise, you can use Recovery Mode (access it from the grub boot menu). This will give you a root terminal that is accessing your installed version of ubuntu (no gui though).

---

