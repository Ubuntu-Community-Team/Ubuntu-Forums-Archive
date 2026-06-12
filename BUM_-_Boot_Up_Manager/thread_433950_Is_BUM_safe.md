---
title: "Is BUM safe?"
date: 2007-05-05
forum: BUM - Boot Up Manager
---

### Post by Bloch on 2007-05-05
I installed BUM and used it to disable printing etc. I got confused as to what I had activated and what I hadn't, so I activated these two
**Scripts for initialising and shutting down the system** (bootclean)
as well as
**User Bootsplash Utility** (usplash)

 - a reasonable choice it might seem. 

When I next booted the system hung after the orange "progress bar" had filled.
I was able to start X windows by ctrl+alt + F1 to a terminal interface and entering
sudo dpkg-reconfigure gdm

This was after a good deal of experimentation. I deactivated the above two 
services and when I next rebooted the system was fine.

But do I have a properrunning system? Shouldn't these essential-sounding services be activated? Were they initially? 
I am confused and want to get my system back to the pre-BUM stage

---

### Post by Mr_Starscream on 2007-05-06
Yer, BUM is a great application and is totally safe.

---

### Post by Bloch on 2007-05-07
Well, gee, that reassures me. Not.

Hvae I endangered my system by disabling
Scripts for initialising and shutting down the system (bootclean)

---

