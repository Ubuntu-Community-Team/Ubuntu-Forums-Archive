---
title: "K3d Error"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-04-01
Hi, I'm having a bit of a drama with a program I tried to install (K3D, a 3D modeling program) - when I tried to install it (or anything else for that matter) I keep getting the error msg about some script returning error exit status 1.

So now, when I try to **_remove_** the program using Synaptic, I get the following error msg:
```
E: k3d: subprocess pre-removal script returned error exit status 1
```
Any idea what this is and how to fix it?

Thanks, you guys... you are the greatest!

---

### Post by johnny4north on 2007-04-01
you have to do some work to fix this :( found solution here at this site - [https://launchpad.net/ubuntu/+source/k3d/+bug/64848](https://launchpad.net/ubuntu/+source/k3d/+bug/64848) You might want to reinstall K3d, then wait for a possible update correction.  or someone might come up with easyer solution{i hope}. good luck Robyn.  check w/ u later.  thank ubuntu

---

### Post by Robynsveil on 2007-04-01
> **johnny4north said:**
> you have to do some work to fix this :( found solution here at this site - [https://launchpad.net/ubuntu/+source/k3d/+bug/64848](https://launchpad.net/ubuntu/+source/k3d/+bug/64848) You might want to reinstall K3d, then wait for a possible update correction.  or someone might come up with easyer solution{i hope}. good luck Robyn.  check w/ u later.  thank ubuntu

Found the solution in the above link - worked a treat! Digested, it's this:

> The patch should be working, but if you are having problems using it you can fix it manually:
- The error is in the file/var/lib/dpkg/status

- So, open the konsole/terminal and do something like:
sudo nano /var/lib/dpkg/status

- Find the entry for the k3d package.

- Now go to the last line of the k3d entry, it is:
Python-Versions: current
- But it should be
Python-Version: current


So, all fixed... thanks for that!!

---

