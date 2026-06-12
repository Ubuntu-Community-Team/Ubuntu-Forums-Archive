---
title: "Kernel-source"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by IDeus on 2006-08-01
I have been at his 2 days and have made little progress. I am trying to make my ipw3945 driver but a prerequisite is the ieee80211. When i try to compile that I get an error saying No suck file or directory for /lib/modules/2.6.15-26-386/build 

I have upgraded and my sources.list is all uncommented. I was finally able to get sudo apt-get install kernel-source to work and now it says I am up to date. I STILL have no build directory though. What am I missing.


Any help much appreciated.

---

### Post by slider on 2006-08-01
Seems some makefiles use a different directory structure, perhaps older. Just create a symbolic link.

ln -s /usr/src/linux-headers-2.6.15-26-386 /lib/modules/2.6.15-26-386/build

---

### Post by IDeus on 2006-08-01
Ok, looks like the headers were not installed. So I ran . remove-old and compiled and it looks good. I also ran make install.

Now when I go to compile ipw3945 I get

Warning: Your kernel contains ieee80211 symbol definitions ans you are not using the kernel's default ieee80211 subsystems 'make install' or have provided a pth to the 1eee80211 subsystem via IEEE80211_INC

If you wish to use the out-of-tree ieee80211 subsystem then it is recommended to use that projects' "make patch_kernel" facility and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in buid warnings and unexpected behavior when running modules which rely on the ieee80211 subsystem


Aborting build,  You can force the build to continue by adding IEEE80211_IGNORE_DUPLICATE=y

to your command line.



any ideas?

---

