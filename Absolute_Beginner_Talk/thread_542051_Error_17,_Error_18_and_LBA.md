---
title: "Error 17, Error 18 and LBA"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Enginer on 2007-09-03
I finally got Ubunto (7.04) running on an old AMD motherboard.  After spending *hours* looking for the solution to my many problems, I realized that an out-of-date BIOS was not very common.

First I got Error 17, which (seems) to indicate Ubuntu cannot recognize my file system.  Actual problem was BIOS HD setting was "Normal" instead of "LBA."  Great.  Easy to fix.

Then I got (about 50 times) Error 18.  This was harder to fix.  Had to repartion drive so that the Linux target partition was small enough for the P5M4-M+ BIOS version V1.05C  ..what ever that is.  I chose 20 Gigs and that worked.

Then I couldn't get internet connection.  Installer recognized the 3Com card, but did not activate it, even though there was no other obvious way to access the Internet. More searching dug out how to enable it, even thougth Fiesty Fawn help system didn't match the System headings initially.

My first experiences with Suse were smoother, and, like others, I wonder why this computer worked well with Windows.  I'm sure I had an 80 Gig HD working in Windows on this same BIOS.
l
I hope this helps someone else save a few hours.  One of the pushes to go to Linux was it's supposed good use of older, underpowered computers.  With BIOS upgrades unavailble...problematic.

---

### Post by louieb on 2007-09-03
> **Enginer said:**
> ...Linux was it's supposed good use of older, underpowered computers.  With BIOS upgrades unavailble...problematic.

BIOS upgrades, if any, will be found on the motherboards manufactures website. Did you look there?

Its a myth that Linux is good for the old low ram computer. I ran Win95 on 32MB ram, 166MHz processor and Win98 on 64MB, 266MHz processor. Not to many modern distros   are going to run  on that. **DSL, Puppy, and Deli** come come to mind as ones that probably would. 

I don't even think xUbuntu would run on that low of ram. Forget even trying Ubuntu or kUbuntu.  Might as well use what they were made for DOS and maybe Win3.1.

If you want a more full featured distro such as Ubuntu  you want some decent hardware 256mb+ ram and a 400MHz+ processor.

---

