---
title: "[SOLVED] how to force architecture on a .pl"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by univremonster on 2007-08-15
I have been fooling around with VMware for the last few hours, trying to get it to work on Fiesty Fawn 64-bit.  I have gotten conflicting advice from people on IRC and on the Forum.  I have tried using the 64-bit version and it said it "cannot find operating system" despite getting various virtual machines from [here]("http://www.easyvmx.com/").  I'm not sure that the 64-bit version is stable, so I would like to try forcing the architecture of 32-bit VMware onto my 64-bit platform.  I have done this before, but only on .deb extensions as per the instructions on [Kilz's post]("http://ubuntuforums.org/showthread.php?p=1174435");

So I have the VMplayer downloaded, and extracted, and the file to install is

vmware-install.pl

How do I force architecture on this file type?  I have tried inserting "--force-architecture" at various places in the install command (which is probably somewhat unintelligent, but I'm a little desperate)

EDIT:  OK so I have tried running this again on 64-bit with some improvements.  I re-downloaded and re-installed VMplayer and the VM.  VMplayer now finds the (64-bit) VM and opens it, but I get an error that the ethernet won't work due to some unsupported ethernet driver (which is fine, I am just trying to run AutoCAD and don't need Ethernet) but then the screen in VMplayer is pitch black.  I don't even have buttons at the top like normal for serial port or parallel port or ethernet.  Curious...

---

### Post by Hospadar on 2007-08-15
You may need video drivers, have you installed proprietary video drivers for your machine?

---

### Post by univremonster on 2007-08-15
I have installed all the restricted drivers

---

### Post by univremonster on 2007-08-16
bump

---

