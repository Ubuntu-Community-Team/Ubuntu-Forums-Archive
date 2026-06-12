---
title: "Ubuntu 6.10 and Parallels Build 3186"
date: 2007-02-28
forum: Apple Intel Users
---

### Post by ebsith on 2007-02-28
I tried searching for this in the forums, but as I am brand new to the ubuntuforums, I may not have entered search criteria correctly - sorry if this has already been asked and addressed.

I just upgraded my Parallels Desktop to build 3186.  I was already having trouble installing Ubuntu before (I've already read the threads addressing the getting stuck at ATP and such) with my old version of Parallels, but now I can't even get the live CD to load.

I configured it as:

Other Linux kernel 2.6

Memory: 512MB
HD: 5000MB

No network connection as of yet, because I'm behind a proxy and that seemed to be a problem when I was attempting to install with the older Parallels.

Anyone else come across the problem?

---

### Post by ebsith on 2007-02-28
So it turns out that if I change the boot order to:  cd-rom, hard disk, floppy  the live-cd works.

Then the same bug fixes as for the last build of Parallels apply (setting RAM to 512MB to avoid getting stuck half way through the install)

---

