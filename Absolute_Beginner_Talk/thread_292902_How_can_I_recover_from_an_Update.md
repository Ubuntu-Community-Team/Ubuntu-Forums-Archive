---
title: "How can I recover from an Update?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by JayTee on 2006-11-04
What's the best way to protect my present configuration and backup my Nvidia driver in case the pending updates I have bork my Xserver which seems to happen to alot of people whenever a new "update" comes out. I've already made a backup of my xorg.conf file but I'm not sure if I'll be able to download a copy of my current Nvidia Linux x86 Kernel Module 1.0-8762. What other config files should I backup?
 The driver version that is listed in Updates is NVIDIA binary XFree86 4.x/X.Org driver new version 1.0.8776+2.6.15.12-1 and there is already a newer beta driver available on the web, version 1.0.9625.

[Edit] Figured it out. I found all the packages I'd installed to get XGL and Beryl working as well as the version of the Nvidia driver I'm using in /var/cache/apt. Backed those onto my external fat volume and backed up my xorg.conf file. Let the Update Manager install the updates and rebooted. So far so good as it looks like I won't have to revert back. Whew!!! Ubuntu rocks but the video tweaking on my system can be a real pain.

---

