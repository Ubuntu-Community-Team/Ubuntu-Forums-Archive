---
title: "Themes missing? Gconf configuration"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Spensawr on 2007-06-18
Hello. All of my icons in the menu on the top left have disapearred and when I go to system>preferences>theme it gives me this error message. 
> 
The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly.

My cd's are also not automounting and I'm not sure if the two are related (I don't see how they could be). Thanks in advance. :D

---

### Post by shearn89 on 2007-06-18
The automounting problem can be fixed by trying to run
```
gnome-volume-manager
```
If (once that is running) cds and things then automount, you know you've solved the problem, so go System -> Administration -> Sessions and add "gnome-volume-manager" to the Startup list.

Not sure about the theme problem.
There may also be a better solution to this than the one i've given you...

---

### Post by Spensawr on 2007-06-18
> **shearn89 said:**
> The automounting problem can be fixed by trying to run
```
gnome-volume-manager
```
If (once that is running) cds and things then automount, you know you've solved the problem, so go System -> Administration -> Sessions and add "gnome-volume-manager" to the Startup list.

Not sure about the theme problem.
There may also be a better solution to this than the one i've given you...

For some reason this doesn't launch my volume control, and it is already on the startup list.

---

### Post by shearn89 on 2007-06-19
It shouldn't launch the volume control - its the gnome interface for detecting and automounting disks, or volumes. I'm afraid i don't have any more ideas, maybe try hunting through the forums?

---

