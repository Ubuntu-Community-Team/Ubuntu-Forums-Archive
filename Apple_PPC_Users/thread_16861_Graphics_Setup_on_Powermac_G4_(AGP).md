---
title: "Graphics Setup on Powermac G4 (AGP)"
date: 2005-02-24
forum: Apple PPC Users
---

### Post by gunug on 2005-02-24
I got through the setup on Warty and have ended up with a BASH prompt; What's the quickest path at this point to getting a GUI interface.  I took a Linux class a year ago (on Redhat not Debian) but I see nothing at the prompt that reminds me of anything that I could use to get into an XWindow setup situation.

---

### Post by gmc on 2005-02-24
[QUOTE=gunug]I got through the setup on Warty and have ended up with a BASH prompt; What's the quickest path at this point to getting a GUI interface.  I took a Linux class a year ago (on Redhat not Debian) but I see nothing at the prompt that reminds me of anything that I could use to get into an XWindow setup situation.[/QUOTE]

Try this:

sudo apt-get install ubuntu-desktop 

You'll end up with a gnome desktop but it's a start. If you have a preference for a different desktop (WindowMaker, IceWM or KDE...) you could try:

sudo apt-get install x-window-system-core; sudo dselect

and then pick and choose your window manager and application software. If this is your first time with Linux, I suggest the ubuntu-desktop method.

Gord

---

### Post by gunug on 2005-02-24
Thanks for the quick reply.  I tried it and got:

       Reading Package Lists. . .Done
       Building Dependency Tree. . .Done
       E: Couldn't find package ubunto-desktop

And then I realized my lack of an African language has led me astray!  Things are happening now!

---

### Post by gunug on 2005-02-25
I have gotten Gnome to work (accidentally).  I used the technique shown in this thread to set it up but I couldn't figure out how to run it.  I powered the machine up and down several times yesterday with it coming up only in the BASH shell and then the end of the work day arrived and I powered it up.  This morning I put the UBUNTU CD into the drive and tried to start it up holding down the C key and I somehow ended up in the graphics shell (GNOME) with a login prompt.  Everything seems to work fine now but I wonder what's up!  Thanks Gord for the helping hand!

---

