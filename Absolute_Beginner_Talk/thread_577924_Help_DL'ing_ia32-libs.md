---
title: "Help DL'ing ia32-libs"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by CHSIsupplier on 2007-10-16
Hi all. I'm running Ubuntu 7.04 (64bit) inside Win Vista with VMware workstation. I'm trying to use this setup for Folding@Home. 

In order for me to install the SMP folding client, I need to install ia32-libs. I tried " **sudo apt-get install ia32-libs** " and it appears to work initially. It goes through some motions (reading depencies, etc.) then says package not found. Does anyone know why this might be. I've run this successfully in my Win XP machine with no hiccups at all. If anyone can help me find some workarounds for this...I would be most greatful!

---

### Post by skymera on 2007-10-16
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install ia32-libs

try that

---

### Post by CHSIsupplier on 2007-10-16
Thanks. I'll give it a go.

---

### Post by Dmart on 2007-10-19
Im doing this for 7.10 and i get the following

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not installable
             Depends: libc6-i386 (>= 2.3.6-2) but it is not installable
             Depends: lib32z1 but it is not installable
             Depends: lib32stdc++6 but it is not installable
             Depends: lib32asound2 but it is not installable
             Depends: lib32ncurses5 but it is not installable
E: Broken packages



any advice?

---

