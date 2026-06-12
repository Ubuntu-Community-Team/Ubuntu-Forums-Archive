---
title: "need help installing windoze"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-06-15
As much at it hurts to say this, I MUST go back to windows for a short duration of time due to project that requires immediate attention.

I dont want to loose my ubuntu however, how do I set up a dual boot?

---

### Post by machoo02 on 2007-06-15
What sort of computer specs do you have?  You could run Windows in a virtual machine if your computer meets some minimum requirements.  Search here on the forums and on the wiki for info on VMWare or [VirtualBox]("http://www.virtualbox.org")

---

### Post by bone43 on 2007-06-15
> **Gmbrdilos said:**
> As much at it hurts to say this, I MUST go back to windows for a short duration of time due to project that requires immediate attention.

I dont want to loose my ubuntu however, how do I set up a dual boot?

Look here...

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

:D

---

### Post by starcraft.man on 2007-06-15
> **machoo02 said:**
> What sort of computer specs do you have?  You could run Windows in a virtual machine if your computer meets some minimum requirements.  Search here on the forums and on the wiki for info on VMWare or [VirtualBox]("http://www.virtualbox.org")

I second Virtual Box. I run a complete windows install off of 512 (you can run it off as little as 256 fine) dedicated RAM (my PC only has 1 GB or regular SD). If I can do it on my ol p4 with 1 GB I think anyone can.

There really isn't anything that can't be done in the VM, Virtual Box has a bidirectional clipboard (copy and paste in and out of it to host), shared folders for moving files in and out and you can network your printer in if you really need it. I don't see any reason any more to have a dual boot except to play games without a hassle. If you have any problems with virtual box feel free to post, I know a lot and got free time :).

Oh and install it via the repos, thats the best way IMO rather than the deb.

---

### Post by Gmbrdilos on 2007-06-16
will my graphics tablet work in it? (works very crappy under ubuntu, too hard to fix)

---

### Post by starcraft.man on 2007-06-16
> **Gmbrdilos said:**
> will my graphics tablet work in it? (works very crappy under ubuntu, too hard to fix)

Is it a USB device? Virtual Box has support for USB, it uses filters and then your device will appear in the VM. I don't know anything about tablets, so can't really know for sure... its a complete windows environment though so it should work fine with whatever drivers you used before long as the device shows up in it.

---

### Post by Gmbrdilos on 2007-06-16
yeah it is USB

my system specs are:
Pentium4 3.0 ghz
1 gig of ram
256 geforce fx5200 video card

---

### Post by starcraft.man on 2007-06-16
> **Gmbrdilos said:**
> yeah it is USB

my system specs are:
Pentium4 3.0 ghz
1 gig of ram
256 geforce fx5200 video card

You got plenty for a VM. Just give xp 512 in the settings menu of Virtual Box and don't do anything too intensive on your Ubuntu machine while its running.

[Download site.]("http://www.virtualbox.org/wiki/Downloads")

You can install from a deb or a repo, your preference. It is very easy to configure, you just open it from the menu push new and follow it. After that, go back in and look at the settings, you'll have to tweak it manually to get it all working. Should do it though, any questions post back :).

---

### Post by Gmbrdilos on 2007-06-16
I was actually considering vista, will 512 be enough for vista?

---

### Post by machoo02 on 2007-06-16
don't bother with vista....I don't think it's worth your trouble.  Just stick with XP.   If you *really* want to use vista, 512 is the minimum that it requires, and you will probably need to turn off all of the Aero effects to get a usable virtual system.

---

