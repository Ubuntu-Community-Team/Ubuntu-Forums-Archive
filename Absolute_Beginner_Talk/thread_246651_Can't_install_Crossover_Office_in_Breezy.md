---
title: "Can't install Crossover Office in Breezy"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by cnayak on 2006-08-29
I get the following error when installing Crossoevr

[I]Verifying archive integrity...OK
Uncompressing CrossOver Office Professional.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


Setup requires an X display to run.  There is a display variable set, however
you have no permissions to access the X server (:0) it points to.
Try running xhost +localhost before su'ing to root.
[/I]

 any idea regarding whats wrong?

---

### Post by desmondo on 2006-08-31
Hi

Before running the installer, try temporarily enabling all local X server connections:

xhost +LOCAL:

This should allow other users to use the X server.
When you have finished installing, this restores your default settings:

xhost -

---

