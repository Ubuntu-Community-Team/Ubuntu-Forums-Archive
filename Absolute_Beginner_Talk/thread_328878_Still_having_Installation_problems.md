---
title: "Still having Installation problems"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by CD Tom on 2006-12-31
Ok, I'm back trying the install again, this time I'm trying it on a Windows XP machine and with the 6.06 version.  I boot from the CD and get the setup or install prompt. I select this and the Loading essential drivers and OK, then it shows Mounting root file system and hangs there.  This Windows XP machines hard drive is formatted FAT not NTSF, I don't know if that makes any difference.  I would sure like to get this to work so I could check it out but so far I haven't had much luck.  Any help would be appreciated.   
Thanks

---

### Post by taurus on 2006-12-31
Can you boot your machine into LiveCD?  You need to use gparted (System -> Administration) to resize your harddrive, leaving a big empty partition at the end to install Ubuntu on!!!

---

### Post by mayonaise15 on 2006-12-31
I know my machine gets stuck at "Mounting Root Filesystem" if I have any sort of portable storage plugged into my computer.  It will hang if it's an external drive, iPod, USB flash drive, or anything similar.

The fact that Windows is formatted as FAT32 shouldn't be a problem at all.

---

### Post by CD Tom on 2006-12-31
I don't seem to know what you mean by Live CD, please forgive my stupidity remember I've never used any Linux before. Also I don't know what you mean by gpart, if I need to partition the hard drive I can do that.

---

### Post by taurus on 2006-12-31
There are three versions of Dapper:  desktop CD (aka LiveCD), alternate CD, and server.  Which version did you download?

Maybe this would give you a hint!

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by CD Tom on 2006-12-31
The machine doesn't have any portable devices attached, the only thing I have attached to this machine is the internet cable to my router.

---

### Post by CD Tom on 2006-12-31
I'm using the Dapper Desktop version.

---

### Post by taurus on 2006-12-31
When your machine boots from the CD, it will go straight into Gnome desktop!  Do you see that?  And if you want to install it, you have to click on the Install icon.  Well, that's what we call LiveCD because you can run Dapper from the CD if you don't want to install it.  Before you click on the Install icon, you need to go into System -> Administration and Gnome Partition Manager (or something similar to that) and use gparted to resize your harddrive, leaving room to install Dapper on.

---

### Post by CD Tom on 2006-12-31
When it boots from the cd I only get the screen with the setup and install option 1, option 2 boot in safe mode (that doesn't work either) there are a couple more options on the screen but they have to do with check CD and something else.  This is really getting fustrating, I've been working in the computer business for 20 years so I have a good idea about computers.  Do you have any other suggestions?
Thanks

---

### Post by Bartender on 2006-12-31
I'd put that CD in another PC.  We need to figure out if the prob is with the CD or something inside your PC that Ubuntu doesn't like.

---

### Post by CD Tom on 2006-12-31
Ok, I've just tried this on my main computer and it seem to load boot from the CD.  Now the other machine is a Celeron 515mhz with 396mb RAM and a 40gig hard disk, with Windows XP pro loaded.  There is nothing else loaded on that machine.  Do you have any ideas?
Thanks

---

### Post by Bartender on 2006-12-31
If you've got broadband, I'd suggest downloading/burning a couple of other distros and see if they work.  Try PCLinuxOS first.
PCLOS went right thru on our main PC, which won't run any Ubuntu-based CD.  Have no idea why.

---

