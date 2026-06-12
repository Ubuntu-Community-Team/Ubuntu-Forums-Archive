---
title: "What hardware changes consitutes a kernel recompile?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by deethree on 2006-11-08
I'm assuming that a motherboard, videocard (GPU), possibly a CPU change/upgrade would warrant a recompile... 

But to just add more RAM would I need to do that?

(Christmas bonus time is looming very close :D )

d3.

---

### Post by nalmeth on 2006-11-08
Nope, no need. Definitely not for RAM or GPU, I've never upgraded my motherboard, but I doubt you'd have to do it for that either.

---

### Post by lowracer on 2006-11-08
I just last night built a brand new system with new everything, including a new motherboard.  No kernel compile was necessary to install on any of it.  The stock kernel on the Edgy LiveCD was all I needed.  Assuming the new mobo is well supported, you shouldn't need to rebuild the kernel.

---

### Post by Blutack on 2006-11-08
Nah, I've never had to recompile.  And unlike certain OS's changing motherboard's does not require re-activation etc.  The only thing is if you are going to upgrade to a 64-bit chip you might want to use the 64 bit kernel - have a look in synaptic/adept.  It will run a lot faster.

---

### Post by deethree on 2006-11-08
Yeah, that was what I was looking for.

The plan is to upgrade from a 2500+ to a nice AM2 ( Dualie ).

Considering my U-install is only a week old, a re-install and being able to bring it up to where it is now isn't much of an issue.

Thanks for the time mates, 

d3.

---

### Post by po0f on 2006-11-08
deethree,

If you just install Ubuntu on the new box you won't have to do anything besides getting binary drivers for graphics cards/wireless/etc.  If you were to try and just move the hard drive into the new box, the kernel will be fine (they're the same for all installs), but you might have problems with some of your configuration files, probably most notably /etc/X11/xorg.conf.

---

