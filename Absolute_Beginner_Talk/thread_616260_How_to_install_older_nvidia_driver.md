---
title: "How to install older nvidia driver?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by dacium on 2007-11-18
I have been having crashes and I found out that the best version for compatibility with my video card is an older version of the NVIDIA drivers. I have downloaded the driver file I need:

NVIDIA-Linux-x86-100.14.11-pkg1.run

But I don't really have any clue how to install this.
I shut down X server and run command:   sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

But the install says no precompiled kernel interface found and tell me I have to compile it. When I says, "yes compile it" the install says: "You do not appear to have libc header files installed on your system"
I have already run apt-get install build-essential also.

How do I install libc header files? thanks!

---

### Post by regor210 on 2007-11-18
I use Envy.
@http://albertomilone.com/nvidia_scripts1.html
Its easy and dose all the work for you.

---

### Post by dacium on 2007-11-18
I found an error with apt-get build install-essential, the cdrom i  was using was bad. Everything works now.

---

