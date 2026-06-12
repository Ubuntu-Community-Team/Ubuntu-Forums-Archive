---
title: "Not letting me install certain codecs"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Bakhman on 2007-11-27
Hi everyone! I just got Ubuntu a week ago and this is my first post on these forums. I'm going to try not using my laptop for anything but the most basic stuff.. but a couple things I do need.

In particular, apparently I need "GStreamer" to to a lot of things like watch video clips. When I try to install the codec it tells me: 

> Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

That last part is what I need clarification on... I went to the manager, but don't know exactly which package is conflicting with GStreamer. I went to the multimedia section, but most of the packages seem to deal with sound. Any way that the average person figures out what the conflicting program is?

---

### Post by XVII on 2007-11-27
Try installing it from Synaptic and see if it will tell you what the conflicting program is.

---

### Post by Bakhman on 2007-11-27
It then says that the following programs have unresolvable dependancies:

gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

I have the Gutsy version, sorry I didn't mention that.

---

### Post by Bakhman on 2007-11-27
Ok I went to the "Repositories" section of the Manager, and checked the box that will allow  proprietary drivers (restricted). However when I reload to apply changes, it comes up with another error:
[I]
W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5[/I]

This error has come up several times actually; any solution aka what is a PUBKEY?

---

### Post by OldTimeTech on 2007-11-27
pubkey is like the windows certificate number

---

### Post by FuturePilot on 2007-11-27
Try this
```
wget http://ubuntu.cafuego.net/AF425CB5.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

