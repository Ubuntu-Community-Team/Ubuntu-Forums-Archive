---
title: "Installing 7.10 X probs..."
date: 2008-02-20
forum: Apple PPC Users
---

### Post by charles.g.moore on 2008-02-20
I have a friends apple emac.  I d-loaded 7.10 and started the install, the screen showed up showing all drivers and network interfaces starting...

After that the X server complained and I got the blue screen...
I noticed that there is an ATI card installed...Does I still have to configure X to work in 7.1 using an ATI card like in 6.06...  

I also noticed that when the boot up sequence (the one with the ubuntu logo and the scrolling services was showing, the resolution looked exptremely tight and small...

Anybody got any ideas?

I just want to get this system up and working for her kids so they can surf the net and play tuxracer etc...

TIA

Chuck

---

### Post by stream303 on 2008-02-21
Hate to say it, but you may have a rough time with Gutsy on an Emac.  Hopefully someone can prove me wrong, but most reports I've seen have been ok with Feisty 7.04 burnt with the "alternate" install image.

Search the threads here for "emac" and you might come up with more help - although I'll do the best I can.

A very nice xorg.conf provided by OswaldKelso can be seen in this thread:

[http://ubuntuforums.org/showthread.php?t=695325&highlight=emac](http://ubuntuforums.org/showthread.php?t=695325&highlight=emac)

---

### Post by charles.g.moore on 2008-02-25
Stream,  thanks for the post...

I took your advice and Feisty installed with no probs...!  Did'nt even have to edit xorg!!!

Thanks again for the help

Chuck

---

### Post by stream303 on 2008-02-25
My pleasure.

For some reason, kids and computers makes me think of restore-disks. :)

Every once in awhile as you add/upgrade packages, I like to run the "aptoncd" utility to help me burn iso's of all my packages so I don't have to download them again from the net after a botched experiment.  It should be in the repositories for a quick synaptic download.

There are other ways to do this, but I dig aptoncd.

Glad you got it running without too much pain!

---

