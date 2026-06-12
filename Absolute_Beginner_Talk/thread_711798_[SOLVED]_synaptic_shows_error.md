---
title: "[SOLVED] synaptic shows error"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by fahadrather on 2008-03-01
after i install  anything from synaptic...i get the following error...
E: swapd: subprocess post-installation script returned error exit status 1
what is this error???

---

### Post by dcstar on 2008-03-01
> **fahadrather said:**
> after i install  anything from synaptic...i get the following error...
E: swapd: subprocess post-installation script returned error exit status 1
what is this error???

Post **all** the information in the message.

---

### Post by fahadrather on 2008-03-01
this is actually "ALL" the information....i get this error every time after synaptic finishes installation..

---

### Post by mikeyphi on 2008-03-01
Looks as though, at some time, you tried to install the package "swapd" which provides for dynamic swap memory. If that is your intention - the installation seems to have an error.

The following might sort the problem:

Open  a terminal and enter the following command

sudo dpkg --configure -a

---

### Post by fahadrather on 2008-03-01
yeah......when i entered the command it showed this
fahad@fahad-laptop:~$ sudo dpkg --configure -a
[sudo] password for fahad:
Setting up swapd (0.2-10) ...
invoke-rc.d: initscript swapd, action "start" failed.
dpkg: error processing swapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 swapd

what to do now??

---

### Post by mikeyphi on 2008-03-01
Try reinstalling the package through Synaptic

Post result!

---

### Post by fahadrather on 2008-03-01
thanx...it doesn't show any error now...

---

