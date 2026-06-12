---
title: "Restricted drivers manager"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by King Riffle on 2007-11-09
Hey guys, 

When I go into "Restricted Drivers Manager" there is "NVIDIA Accelerated graphics driver (latest cards)" in it that is not in use. When I try to enable it it shows this error: 
"The software source for the package

   nvidia-glx-new

 is not enabled."

Why is that?

PS: I have a GeForce 8500GT and am running Ubuntu 7.10

---

### Post by misfitpierce on 2007-11-09
try this in terminal

sudo apt-get install nvidia-glx-new

---

### Post by King Riffle on 2007-11-09
I get this in terminal:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate"

---

### Post by Seisen on 2007-11-09
you need to enable the restricted repository.
System > Administration > Software Sources. Check "Proprietary Drivers for Devices (Restricted)" box

---

