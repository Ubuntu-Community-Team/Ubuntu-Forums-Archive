---
title: "Ubuntu on Bondi Blue iMac"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by TonyKZ1 on 2007-05-10
Hello all, I'm installing this distribution on my son's iMac, a G3 @ 233MHz with 256MB Ram, 20GB hard drive. This is a dual boot system with Mac OS 8.1 on the mac partition. I've booted up off of the live CD, no problems, then I ran the installer, no problems. I've got it installed now, however when we turn the iMac on, it goes to a blue screen, no yaboot screen. I can boot to the open firmware screen, by holding down cmd+opt+o+f. I've also tried the Xbuntu & Kbuntu versions with the same results. I thought it was kinda odd that it boots fine from the live CD, but won't from the hard drive. I've read the FAQ, searched for anything related but haven't found the answer yet.
Any ideas/suggestions?
Thanks, Anthony Bailey

---

### Post by stmiller on 2007-05-10
Ah crap okay sounds like the installer did not write the yaboot config to the boot partition correctly.

To fix this, run the ubuntu installer from the cd (again), then at the end of the install BEFORE rebooting, hit Ctrl-Alt-F1 (or F2) to get to a command line. And type

yabootconfig

and that should build a correct /etc/yaboot.conf file.

Then run 

ybin -v

to write those changes to disk.

This *should* work, assuming yabootconfig is on the install cd...

---

### Post by TonyKZ1 on 2007-05-10
Okay, will do.
Thanks, Anthony Bailey

---

