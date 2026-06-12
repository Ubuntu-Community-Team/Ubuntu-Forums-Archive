---
title: "Update manager just updated....now NO GUI"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by rallenk on 2007-08-18
I just finished a large (609 files) upgrade through Update Manager...supposed to be Ubuntu 7.2
I then rebooted and it would not boot to GUI. 
Did I miss something?

Bob:confused:

---

### Post by walkerk on 2007-08-18
> **rallenk said:**
> I just finished a large (609 files) upgrade through Update Manager...supposed to be Ubuntu 7.2
I then rebooted and it would not boot to GUI. 
Did I miss something?

Bob:confused:

so your at xterm? try starting x
```
startx
```

?

---

### Post by Zalbor on 2007-08-18
Does that mean you were in Edgy and upgraded? If so, try
```
sudo dpkg-reconfigure xserver-xorg -phigh
```.

---

### Post by rallenk on 2007-08-19
> **Zalbor said:**
> Does that mean you were in Edgy and upgraded? If so, try
```
sudo dpkg-reconfigure xserver-xorg -phigh
```.
No...update from within Fiesty 7.04

It tells me this:
"Failed to start x server. It is likely it is not setup correctly. Would you like to view x server to diagnose problem?"
I enter 'yes' ....I find these errors and warnings...

(ww) open ACPI failed
(ee) module ABI minor version (2) is newer than servers version (1)
(ee) no drivers found

"Fatal servor error: no screens found"
I then enter on "OK" and get this:

The x server is now disabled. Restart GDM when it is configured correctly.

So, what needs to be done?

This was an automatic Update from my panel inside Fiesty 7.04

---

