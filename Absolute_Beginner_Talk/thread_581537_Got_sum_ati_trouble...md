---
title: "Got sum ati trouble.."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by steffstar on 2007-10-19
I was wondering if there were any kind souls out there willing to help out a brand new "sick of windows-viruses so I converted to linux"-ubuntu-user.. or something like that.

Problem is..
I'm trying to install some new drivers for my ATI Radeon x700 pro graphics card, so I downloaded the linux drivers from ati. And from reading a couple of posts here I've come to understand that this is what I'm supposed to type to make it work:

*[COLOR="DarkGreen"]sudo sh ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/7.10[/COLOR]*

And then this is what happens:

[I][COLOR="DarkGreen"]Created directory fglrx-install.Vc8524
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.40.4..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/7.10
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.Vc8524[/COLOR][/I]

So if anyone has any idea of what I'm doing wrong, please help me :)

 - Ubuntunoob

---

### Post by Pumalite on 2007-10-19
What are your specs?
Do you have build-essential installed?
Do you have proper headers?

---

