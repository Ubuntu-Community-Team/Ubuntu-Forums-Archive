---
title: "Change Ubuntu to run in console instead of X"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by fhqwhgad on 2007-12-20
I installed the desktop version of Ubuntu (and i do want X from time to time) but will actually rather run it in console, without X started up.
The problem though, is that whenever i close down gnome it reboots. It wont let me exit gnome and continue running in console mode, like it was a server install.
Can i fix this somehow?
I want to run it as server but keep X in so i can startx if i need to.

---

### Post by LowSky on 2007-12-20
what happenes if you remove gnome-desktoip from the bootup manager?

you could change grup to boot to recovery mode instead of normal

---

### Post by fhqwhgad on 2007-12-20
Bootup manager? Where do i find the bootup manager? The grub files?

---

### Post by Phesto on 2007-12-20
You can edit the /etc/inittab file
The beginning of the file should look like below
```

#
# inittab       This file describes how the INIT process should set up
#               the system in a certain run-level.
#
# Author:       Miquel van Smoorenburg, <miquels@drinkel.nl.mugnet.org>
#               Modified for RHS Linux by Marc Ewing and Donnie Barnes
#

# Default runlevel. The runlevels used by RHS are:
#   0 - halt (Do NOT set initdefault to this)
#   1 - Single user mode
#   2 - Multiuser, without NFS (The same as 3, if you do not have networking)
#   3 - Full multiuser mode
#   4 - unused
#   5 - X11
#   6 - reboot (Do NOT set initdefault to this)
# 
id:5:initdefault:

```

Change 
```
id:5:initdefault:
```
to
```
id:3:initdefault:
```

This will allow you to boot to the terminal and if you need then startx from there.

---

### Post by fhqwhgad on 2007-12-20
> **Phesto said:**
> You can edit the /etc/inittab file
The beginning of the file should look like below
```

#
# inittab       This file describes how the INIT process should set up
#               the system in a certain run-level.
#
# Author:       Miquel van Smoorenburg, <miquels@drinkel.nl.mugnet.org>
#               Modified for RHS Linux by Marc Ewing and Donnie Barnes
#

# Default runlevel. The runlevels used by RHS are:
#   0 - halt (Do NOT set initdefault to this)
#   1 - Single user mode
#   2 - Multiuser, without NFS (The same as 3, if you do not have networking)
#   3 - Full multiuser mode
#   4 - unused
#   5 - X11
#   6 - reboot (Do NOT set initdefault to this)
# 
id:5:initdefault:

```

Change 
```
id:5:initdefault:
```
to
```
id:3:initdefault:
```

This will allow you to boot to the terminal and if you need then startx from there.

Is it bad if i don't have an /etc/inittab? Can i just copy what's in yours into a new one, and then that will fix it?

---

### Post by Fixman on 2007-12-20
> **fhqwhgad said:**
> I installed the desktop version of Ubuntu (and i do want X from time to time) but will actually rather run it in console, without X started up.
The problem though, is that whenever i close down gnome it reboots. It wont let me exit gnome and continue running in console mode, like it was a server install.
Can i fix this somehow?
I want to run it as server but keep X in so i can startx if i need to.

Or, if you want a "bigger" console, you can press crtl-alt-f1 (or any f from 1 to 6) to go to a tty, that is a big console. You can get back pressing ctrl-alt-f7.

---

### Post by BobCFC on 2007-12-20
> **fhqwhgad said:**
> Is it bad if i don't have an /etc/inittab? Can i just copy what's in yours into a new one, and then that will fix it?



I believe inittab is the old way and has been replaced by upstart.  Did a quick search no inittab on my Gutsy either.


EDIT:  [here is a thread]("http://ubuntuforums.org/showthread.php?t=166390") with the info that you need.  Good luck

---

### Post by Mike_Longbow on 2007-12-20
Try this.

```
sudo update-rc.d -f gdm remove
```

That should prevent GDM to start everytime you boot, and leave you with just a console. From there you could startx to start Gnome, of if you want to start GDM:

```
sudo /etc/init.d/gdm restart
```

If you ever want to go back to how it was, do the oposite:

```
sudo update-rc.d gdm defaults
```

---

### Post by fhqwhgad on 2007-12-20
> **BobCFC said:**
> 
EDIT:  [here is a thread]("http://ubuntuforums.org/showthread.php?t=166390") with the info that you need.  Good luck

This was exactly what i needed, thank you kindly.

---

