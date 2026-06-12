---
title: "[SOLVED] Wine - the devil"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-08-18
Hi there,

Does any one know where Wine stores it's temp files during an install? Where is a user's temp folder?  When I double clicked the setup.exe file - it seemed as if wine was starting the setup as root!? there was a "starting administrative application" dialog on the task bar. Is there any way to keep this from happening?

Thanks for any help!

Rudolf

---

### Post by Happy_Man on 2007-08-18
Wine config stuff can be edited through the command "winecfg". It keeps install stuff under the directory ~/.wine.

---

### Post by RudolfMDLT on 2007-08-18
Wine ran as root and installed all 5 gigs in root's home folder, filling up the drive and keeping GDM from loading. Anyway - found the offending folder and deleted it.  GDM still doesn't load but Iill take that up else where. 

Thanks Happy_Man!

Anyway - I'll mark this thread as resolved but if anybody still feels up to it:

1) Where is a users temp folder?
 2) Where does Ubuntu store and App's temporary files?

---

### Post by schorsch on 2007-08-18
> **RudolfMDLT said:**
> 
1) Where is a users temp folder?
 2) Where does Ubuntu store and App's temporary files?
Normally all this stuff is stored under the /tmp directory. As on all debian based systems this directory is cleaned at boot time do not use the /tmp directory to store files that you want to use after the next reboot .. :-)

---

