---
title: "Error message re: Synaptic Package Manager"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by healthpellets on 2007-01-27
I got this error message when i last ran the package manager:  

E: clamav-base: subprocess post-installation script returned error exit status 1

um, help?  (i was installing wifi radar, if it matters)

---

### Post by riven0 on 2007-01-27
Do you have any broken packages? Check there first and try to get it fixed. If not, try to force the install of clamav-base:

> sudo apt-get install -f clamav-base

---

