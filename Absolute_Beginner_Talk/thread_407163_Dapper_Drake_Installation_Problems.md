---
title: "Dapper Drake Installation Problems"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by worldshaper on 2007-04-11
I am currently trying to build a VMware Server Host machine for my company as a first step into virtualization.  I am trying to install 6.06.1 LTS Server on a Dell SC1420 (single xeon 2.8ghz/800, 3GB RAM, 250GB x2 SATA) but the install keeps failing at the "Load debconf preseed file" step.  

I recently (as in two days ago) successfully installed the same release (burned from the same .iso) on an HP Proliant 330 G3 without a problem.  I have tried both the x86 and 64-bit versions of 6.06.1, as well as trying the trick of burning the CD at x4 speed on a CD-R.  Still nothing.  

I tried to "Load installer components from CD", but it eventually errors out after sitting at "Retrieving apt-cdrom-setup" for a minute.  I get the error message "Failed to copy file from CD-ROM.  Retry?".  Answering "yes" gets me nowhere.

I've done searches on both the forums here and google, and I can't find anything (well, some obscure references to russian websites...).

Suggestions, anyone?

---

### Post by mohjlir on 2007-04-12
Have you tried doing a net-install? If you have a suitably quick internet connection, you can get a fairly minimalistic boot cd image that has the bare bones required to get on the internet and download the rest of the operating system. You could try that, or, if you are willing to try a different distribution I could sugest debian etch. It worked for me just fine (created VM on Windows Vista).

---

### Post by worldshaper on 2007-04-12
Hey, thanks for the information.  

Next question: How exactly would I do a network-install from the internet?  I've done a search online, but I only come up with documentation on doing a network-install from a local tftp server.  You mentioned:

> boot cd image that has the bare bones required to get on the internet and download the rest of the operating system

Any documentation out there on how to do this?

---

### Post by worldshaper on 2007-04-12
OK, well, I feel kinda silly.  It turns out that the CD-ROM drive in the server was bad, which is why it wasn't reading the ubuntu install disc.  Strange thing, though, it has been slowly degrading over the last couple of days, until now it wont even boot from CD.  I replaced the CD-ROM drive with an old spare I had lying around and everything works great.  Oh, well, I should have remembered to check my hardware... tech support 101 and all.

Fortunately it looks like I will get to use Ubuntu after all! :D

---

### Post by LaurelLynn on 2007-04-12
Dear worldshaper,

Don´t blame yourself. I can´t count the number of times I´ve seen myself and others run all over the place trying to fix something that turned out to be flakey hardware.

Sounds like the laser is out of alignment, or the bearings are wearing down.  Either way you probably want to replace the drive. In a business setting I replace any drive that so much as hiccups. They are cheap enough, that it is not worth risking valuable company data, trying to fix/live with them.

---

