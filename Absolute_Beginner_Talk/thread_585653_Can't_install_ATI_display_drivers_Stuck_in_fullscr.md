---
title: "Can't install ATI display drivers/ Stuck in fullscreen with a widescreen monitor"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by NeMeSiS187 on 2007-10-21
Soo, I finally got Gutsy installed on my Thinkpad T60 with an ATI X1400 video card (I had to use the alternate CD just to get it installed) and now that it's up and running I can't seem to install ATI video drivers and get my screen to appear widescreen.

When I do sudo apt-get install xorg-driver-fglrx it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xorg-driver-fglrx has no installation candidate

When I try to install the drivers from the restricted drivers it says the software source for xorg-driver-fglrx isn't enabled. Any ideas as to how I can fix this?

---

### Post by Kingsley on 2007-10-21
Make sure none of the links in your repository are commented out. Open up /etc/apt/sources.list to check.

---

