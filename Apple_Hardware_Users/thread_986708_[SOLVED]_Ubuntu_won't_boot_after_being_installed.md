---
title: "[SOLVED] Ubuntu won't boot after being installed"
date: 2008-11-18
forum: Apple Hardware Users
---

### Post by Danny Shumway on 2008-11-18
After a lot of trouble with some different versions, I finally downloaded Ubuntu 8.04 Hardy Heron from here -

[http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-alternate-powerpc.iso)

for my Powerbook G4.  I burned the image to the disk and installed it, wiping out everything else (I don't really want anything but linux on that computer).  It installed perfectly, not an error message to be found.  At the end, it ejected the CD and restarted.  Now the problem came though.  Ubuntu goes through a couple of screens saying it is going to boot, then says loading please wait for about 1 second on the top of the screen, then goes black except for a slight hard to see white bar near the bottom, with a nice gradient off of it going down. 
No error message or anything.  I've tried this multiple times and nothing changed.   Any suggestions?  I've never used any linux before, this was the first one that installed for me, and I'm afraid my computer knowledge as far as macs go is quite limited.  I don't go much farther than actionscript and a little C++, and I don't see how that would relate to installing ubuntu....
Ubuntu should be the only operating system on there, I'm almost sure I selected the option to wipe off the hard drive when installing it.
please help, Ubuntu looks really great.

---

### Post by tygoerlitz on 2008-11-18
Hey you can try this I had a similar problem with my ibook, check out my thread. In the second stage boot, hit tab to disable the countdown and type in

Linux video=ofonly nosplash

see what that does for you

---

### Post by Danny Shumway on 2008-11-18
Thanks, I'll try it now.

---

### Post by stream303 on 2008-11-19
Also let us know what model of G4 Powerbook you are using:

[http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html](http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html)

This will help to figure out if you have an ATI Rage or Radeon card, and what options you may have to manually configure...

---

### Post by Danny Shumway on 2008-11-19
It worked perfectly!  Thank you so so much!  The command got it to boot up right.  I had some trouble until I told it to start the session under compiz, I think, or something similar.  I'll check.  
I'm not sure what version the laptop is, but I'll check up on it.  Will powerpc ubuntu support wireless internet if I have to install the drivers and everything?
And is there any way to set that as a permanent command for yaboot so I won't have to reenter it over and over again?

---

### Post by Danny Shumway on 2008-11-19
Okay, I'm using GNOME for my desktop but I'm still not sure what kind of powerbook I'm using.  How do I find out?

---

