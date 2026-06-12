---
title: "Can't enable Restricted Nvidia Driver"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dsmorgan6922 on 2007-10-18
I just installed 7.10 onto my T61 laptop and am trying to enable the restricted driver for my Nvidia Quadro NVS 140M card to get the 3d effects. When I click to enable the driver I get the following error:
> 
The software source for the package
nvidia-glx-new
is not enabled.


I tried to do a sudo apt-get install nvidia-glx-new to get it and
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate


Any help?

---

### Post by dmilner on 2007-10-18
You'll need to go to the Software Sources and enable the correct Repository.  I'm sorry, I don't know which one, so I guess that you could just try enabling all of them.

I'm new at this, so I don't know a whole lot yet.

---

### Post by Xgkkp on 2007-10-18
I had this same problem, and fixed it my enabling multiverse.

Except now all I get is a blank screen when I try to boot :(

---

### Post by CR055 on 2007-10-19
Exact same problem and I can't get anything to work.  :(

---

### Post by JacobRogers on 2007-10-22
Go to System>Admin>Software sources and enable the restricted reposatories.  That worked for me!

---

### Post by cyber5 on 2007-10-24
> **JacobRogers said:**
> Go to System>Admin>Software sources and enable the restricted reposatories.  That worked for me!

You = win. 

Have a gold star:  :KS

---

### Post by Crafty Kisses on 2007-10-24
Envy.

---

