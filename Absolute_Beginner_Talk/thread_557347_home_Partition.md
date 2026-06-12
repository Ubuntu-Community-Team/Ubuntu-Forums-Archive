---
title: "/home Partition"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-09-22
Hi all,

At the  advice of some on this forum, when I installed Ubuntu to dual-boot on my computer, I created a separate partition for the /home directory. As I understand it, this will allow me to re-install if I screw something up, or do a clean install to Gutsy without losing my data. Sounds good.

My question is, how far does that go? Could I install, say, Linux Mint on the computer, replacing Ubuntu, and then have my desktop settings, Open Office settings, etc. recognized? How about PCLinuxOs, or pure Debian, or an RPM based distro like OpenSuse? 

I'm mostly just curious, but I was also thinking, when it comes time to upgrade to Gutsy, I might do a clean install of a few other distros to check 'em out, and was wondering what would happen.

---

### Post by rsambuca on 2007-09-22
Your /home folder contains, among other things, the settings for your programs and desktop.  If you use the same /home for gutsy, you should be fine.  If you use the same /home for another distro, it will *usually* work, but not necessarily work smoothly.  Most of the program settings will be fine and work, but for some programs, the files don't seem to be in the right spot, or they just don't seem to work 100%.  It shouldn't completely wreck anything though, so you should be ok to try it!

---

### Post by rich.bradshaw on 2007-09-22
Yep, /home contains everything that you ever have changed. (except for when you were sudoing!).

---

### Post by Duck2006 on 2007-09-22
> **rsambuca said:**
> Your /home folder contains, among other things, the settings for your programs and desktop.  If you use the same /home for gutsy, you should be fine.  If you use the same /home for another distro, it will *usually* work, but not necessarily work smoothly.  Most of the program settings will be fine and work, but for some programs, the files don't seem to be in the right spot, or they just don't seem to work 100%.  It shouldn't completely wreck anything though, so you should be ok to try it!

Very nice to know thanks

---

### Post by vanadium on 2007-09-22
DO NOT share your /home over different operating systems. It might and will work to some extend, but it is not designed to work like that.

---

