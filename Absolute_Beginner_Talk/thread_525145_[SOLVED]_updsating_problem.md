---
title: "[SOLVED] updsating problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by vinu76jsr on 2007-08-14
when i run command 
sudo apt-get update
it says :

[I]E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/I]

I think this is some kind of resource unavailability problem 
I want to override this error because it is annoying 

help me!!!!!!!!!!!1

---

### Post by RomeReactor on 2007-08-14
Hi. I think that message is telling you that there's another process using the list, whether it's Update Manager running in the background, or if you have Synaptic or Add/Remove open. Close any of those if they are open--or wait a few minutes in the case of Update Manager--and try again.

---

### Post by vinu76jsr on 2007-08-14
it seems what u said thanks 
I also skipped language packs 
they were causing problem in synaptic 
now graphical install works fine after cleaning the mesh.
thanks!!!!!!!!!!!!!

---

