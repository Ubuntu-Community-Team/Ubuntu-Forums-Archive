---
title: "Seeking guidance: Using Ubuntu for Virtualization"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by UbuntNic on 2007-12-15
I'm a Windows-guy who knows *nothing *about Ubuntu; even spelling it correctly is a challenge for me. But I have lofty goals. I want to:

[LIST]
[*]Install Ubuntu on an old but reasonably powerful desktop computer (P4, 2.2GHz, 2GB RAM, 80GB HD)

[*]Install VMWare (or some other virtualization layer) on the base Ubuntu install.

[*]Install other operating systems on the virtualization layer, including a GUI-based Ubuntu desktop, Windows 2003 Server, and a Windows 2008 Server Beta or Release Candidate. I'm not interested in performance or production-level reliability; I'm just evaluating functionality right now -- will it all actually *work*?[/LIST]

I'm sure I'll have oodles of detailed questions as I proceed and I hope I've come to the right place for help. What I need now is a little direction. For example:

[LIST=1]
[*]Should I use a server version or a desktop version of Ubuntu for the base install? Which version?

[*]Considering what I have in mind, is VMWare the best virtualization solution? Which flavor or version? (Free would be best but I'm not totally opposed to investing a little in this effort.)

[*]Does what I'm trying to do make sense? Am I biting off more than anyone can chew, much less a newbie
like me?[/LIST]

Whatever guidance anyone can offer will be appreciated.

UbuntNic (a hopeful/optimistic name if ever there was one.)

---

### Post by Dr Small on 2007-12-15
I did something very similar to this, on my other 80GB hard drive.
I installed Ubuntu Server, then Xorg and VirtualBox. Then you can have VirtualBox fullscreen, and won't have to worry about gnome-panels or whatnot.

It worked great for that, and since X is fairly light, it didn't use much RAM when running the Virtual OSes. (It practically just used RAM for the VirtualOS, rather than the system.)

Dr Small

---

### Post by UbuntNic on 2007-12-15
> **Dr Small said:**
> I did something very similar to this, on my other 80GB hard drive.
I installed Ubuntu Server, then Xorg and VirtualBox. Then you can have VirtualBox fullscreen, and won't have to worry about gnome-panels or whatnot.


Thanks Doc! I'm floored to have gotten a useful, sensible reply so quickly. I even understood some of the words you used!

I was thinking about VMWare because I figured I'd find some detailed, step-by-step tutorials for installing it on Ubuntu. I found them, alright, but they left me with more questions than they answered. A quick Google of VirtualBox, however, turned up something right on point: [Installing Virtualbox and Windows on Ubuntu]("http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/"). So I'm good to go. 

Well ... except for those little details like actually getting Ubuntu installed and working, and figuring out what Xorg is and why one would need it.

Meantime, if anyone else has comments or suggestions, I'd sure like to hear them.

UbuntNic

---

