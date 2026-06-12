---
title: "can't shut down the PC"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Tentacel on 2006-01-15
Hello

I installed via synaptic "wdm" and said then, that I want to use wdm instead of gdm. That was a big mistake. At first the login screen changed and now I can log off from my session, but I can't shut down the PC. 
The procedure how I shut down my PC since then: shell -> sudo gdm
(I think a new X-Server starts) -> then the old gdm login screen appears -> and from there I shut down the PC
Somehow I can't uninstal wdm via synaptic :confused: 

My question: How can I restore the gdm login screen / interface

Thank you for the answers

---

### Post by stuporglue on 2006-01-15
Try running
$ sudo dpkg-reconfigure gdm

and see if that gives you the option. 

Otherwise remove gdm and wdm and then reinstall gdm using synaptic or your favorite package manager interface.

---

### Post by Tentacel on 2006-01-15
Thank you, that worked
:D

---

