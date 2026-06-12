---
title: "[solved] H E L P !!!!!!!!!!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-10-26
I don't know what I've done, so I'll try to explain.  I downloaded the source for an application and when I tried to compile it it said it needed gtk+2.  I went looking on the net and found gtk+-2.10 and downloaded the source.  It came up with a BUNCH of things it said it needed.  So, I ended up downloading a TON of things and "make" ing each one until I got back to gtk.  It got down to were it said it was missing x development libraries.  I  went to synaptic and marked glade as I knew it was one of the things that was needed.  It in turn marked a TON of stuff, including the things I had already downloaded and all inds of x development stuff.  This is when my problem started.  I rebooted the system, and when it gets to the logon screen, instead of seeing a logo splash and the prompt, I just get a blank icky-yellow screen with the mouse pointer in the circle (indicating sytem busy).  I am able to do a ctrl/alt/F1 and log on to a terminal session, but I can't get to a windowed session.  Right now I'm running off my dual-boot Windows so I could post this.  How can I correct this (or even have any idea what the heck is happening) short of reinstalling Gutsy?

Thanks in advance for helping a dumb guy out!:)

---

### Post by alienexplorers on 2007-10-26
Try from ctrl/alt/f1:
> sudo dpkg-reconfigure xserver-xorg
and reboot

---

### Post by anewguy on 2007-10-26
Thanks for the reply.  Same thing happens (except the default screen resolution is lower because I didn't select the higher one).  Starting to feel like a reload - I get errors in terminal, and errors when it shutsdown.

---

### Post by BrendanM on 2007-10-26
Yikes, sounds like something went pretty wrong. How come you were installing from source? Is the program you need not available in the repositiories anywhere? Installing from source is inherently trickier/has more potential to go wrong than getting things from the repositiories or downloading a .deb package.

Other note: Isn't Gutsy supposed to have a "bulletproof X" that prevents stuff like this from happening?

---

### Post by anewguy on 2007-10-26
Source is for ops-for-linux from sourceforge.  While it comes with a binary, it has a flaw and I need to make a small change in the source and recompile.  Same thing for pv2tools-linux also from sourceforge (they're both under saturntools).  They want libraries that aren't installed by default.  I thought I could get by, and was doing great, until I did that dumb x thing.  I think I'm going to have to reinstall Gutsy from scratch again, and this time go through synaptics for glade and it's dependencies before getting the other stuff and see what happens.

---

### Post by evilregis on 2007-10-26
Did you check the repos for the packages you needed to resolve the dependencies?  Even if you have to compile from source, it's best to get all that you can out of the repos and compile as little as possible.

I've been fortunate enough to not have to compile anything for a couple years now.  Last thing was for an Aureal sound card and every time seemed like a crap shoot.  Could work or could completely tank the system.

Perhaps you could just try reinstalling X instead of reconfiguring it?

---

### Post by anewguy on 2007-10-26
Yeah, I checked first but I must not have used the correct search string.  I was looking for gtk, but must have messed something up.  I think my best bet now is just to reload and go.

Thanks for the help, everyone!:)

---

### Post by Threbus5 on 2007-10-27
Yes, sure appears that a reinstall is your next resort.

You could install a working Ubuntu and then tar from your backup. That would at least return you to the baseline prior the present debacle.

Because my systems suffer frequently from experimentation I keep two separate backups of the machine for just the circumstances that you encountered. 

Take care.

---

