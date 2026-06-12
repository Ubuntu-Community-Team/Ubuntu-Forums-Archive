---
title: "I'm dumb, cant install"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by trus-rod on 2006-03-01
Hi there, I'm a rookie here.  I know nothing but windows, I have an old computer, PIII (566 celeron) w/ win98 that Ive been playing around with.  Since I haven't blown it up, I thought I'd like to try a new operating system and make my garage computer.

I've downloaded the disk, burned it with the iso recorder, I did this on an xp machine.  Now when I put the disk in the Garage computer, nothing happens.  Reboot, and it just loads windows.  I can see all the file on the disk.  Where'd this dummy go wrong?  Does it have something to do with the ntsf file system on the xp machine, and fat32 on the other one?  Should I reformat first?

Lost
Trus

---

### Post by gingermark on 2006-03-01
Log into your BIOS and check your boot order. Make sure you're trying to boot off your CD before you try to boot off your harddrive.

---

### Post by Iandefor on 2006-03-01
Some computers aren't set to boot off of CD before the hard drive. Fix this by going into the BIOS (If you don't know how, during startup, it should say something like "press [F2] to go to setup"- setup is the BIOS setup program)
Look around for a boot order setting, and get it set up so that it checks the CD drive before the hard drive. Save settings and exit. It'll either work then or on the next reboot. 

Oh, and just because you're new don't mean you're dumb :-D.

---

