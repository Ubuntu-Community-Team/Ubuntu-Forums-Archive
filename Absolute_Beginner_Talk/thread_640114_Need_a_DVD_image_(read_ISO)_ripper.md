---
title: "Need a DVD image (read: ISO) ripper"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Bakhman on 2007-12-13
I've checked out at least 5 programs so far from other threads; including acidrip, DVDshrink, OGM...
All I want to do is rip the ISO image file onto my desktop; that's my only criteria and these programs are not letting me do it. And if they can, someone needs to point out the option for me...

I'm aware of right-clickin the DVD file, but the ISO file turns out to be 6 gigs! Too big to put on a blank DVD and there are no option! :(

---

### Post by Dark_Stang on 2007-12-13
Try Graveman.

---

### Post by Bakhman on 2007-12-13
I got it, but for the installation it says:

Basic Installation
==================
  First, make sure you have compiled and installed the dependencies.
  Most recents Linux distributions will include them, except maybe
  for libid3tag

And I dont know what how to "compile and install" dependencies...

---

### Post by fenian on 2007-12-13
Try K9copy.

---

### Post by Dark_Stang on 2007-12-13
> **Bakhman said:**
> I got it, but for the installation it says:

Basic Installation
==================
  First, make sure you have compiled and installed the dependencies.
  Most recents Linux distributions will include them, except maybe
  for libid3tag

And I dont know what how to "compile and install" dependencies...

Graveman is available through synaptic, you don't need to compile from source. Just go Applications > Add/Remove programs and search for it. You might have to enable the extra repositories first. System > Administration > Software Sources then check everything on the first page except for the CD.

---

### Post by Bakhman on 2007-12-13
Ok I got Graveman to work - thanks - but when I said to make an ISO of the DVD, it immediately pops up with this error:

/usr/bin/mkisofs: No such file or directory. Invalid node - '/media/cdrom0/AUTORUN.INF'.

How do I change the directory...? I don't remember ever specifying that folder.

---

### Post by Bakhman on 2007-12-13
BTW I tried K9copy, and I am unable to install/compile it.. it seems complicated though it looks like the perfect program.

---

### Post by Dark_Stang on 2007-12-13
K9copy is also available through synaptic.

I just tested it and got an error too... O.o For some reason you have to be root to use it. Strange.

---

### Post by fenian on 2007-12-13
I just posted instructions for compiling the latest k9copy [here.]("http://ubuntuforums.org/showthread.php?t=400570&page=6")

---

### Post by Bakhman on 2007-12-14
Sweet thanks SO much guys, looks like K9 was exactly what I needed.
Now time to uninstall those other 8 or so worthless programs.

---

### Post by hyper_ch on 2007-12-14
k3b  is an excellent burning program that also allows you to create .isos

---

### Post by bigken on 2007-12-14
try Gmout-iso this will mount the iso a folder of your choice :)

---

### Post by rockinlinux on 2007-12-14
> **hyper_ch said:**
> k3b  is an excellent burning program that also allows you to create .isos

+1

and k9 is great too

---

