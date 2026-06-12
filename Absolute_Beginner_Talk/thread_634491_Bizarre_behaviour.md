---
title: "Bizarre behaviour"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-12-07
I've just been trying to install Xubuntu on an old IBM Aptiva running Win98SE and as the install disk is doing its thing, it gets to a point where it comes up with a message "hda lost interrupt" and hangs for a while and then repeats the message. This goes on four times and then it does some more things before it gets to the "lost interrupT: message again.
Thinking this could be a problem with my CD, I tried the same thing with several other distros that I have and got the same result.
I even got the same result using two different versions of Gparted.
So, just to prove that the hard disk itself was OK, I used the MS fdisk and completely wiped the disk, then created a new primary DOS partition so that I could re-install Win98.
This re-install went without a hitch, so when I finished, I went back to the Linux CDs and got exactly the same behaviour as before.
This is obviouslly a hardware problem, but what? Has anyone else experienced this behaviour?

---

### Post by celticbhoy on 2007-12-07
What are the specs on the PC

---

### Post by tonymoloney on 2007-12-07
Sorry. Its got 256Mb RAAAM and 5Gb hard disk. Not sure about the processor right now.
I even got this behaviour when trying to run the Puppy Linux live CD, which eventually got up after waiting through about 5 cycles of the lost interrupt messages, but patience didn't win out with any of the other distros (Xubuntu, Fluxbuntu, Gparted, DreamLinux).

---

### Post by mgmiller on 2007-12-07
I would be more suspicious of the hard disk controller than the drive itself.  
See if you can find out what chipset is used.  It may be one that has poor Linux support.

---

