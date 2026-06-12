---
title: "Boot Problems"
date: 2007-12-20
forum: Apple PPC Users
---

### Post by jjhappypants on 2007-12-20
Hey-
I have a PPC Mac Mini that I've been trying to get Ubuntu 7.10 on.  I tried the live CD, but the boot sequence froze at "Running local boot scripts (/etc/rc.local)".  Unlike other cases I read about like this, pressing enter or ctrl C did nothing.  I then tried using the alternate install disk, and though it installed fine, on booting the operating system for the first time it froze in the exact same spot.  

After reaching this spot it always flashes slowly from the boot screen to black and back again, until it finally just rests on the boot screen.  And doesn't move.  Please help! :(

---

### Post by rexxxlo on 2007-12-25
i am having this problem too i will bump it up to hopefully get it some attention

---

### Post by xxyyeah on 2007-12-27
Once I also met this problem. Maybe you can try this way:
ctrl+alt+f2
sudo dpkg-reconfigure xserver-xorg

---

### Post by mwille14 on 2007-12-28
I am also having problems with v7.10 at running bootscript. I have G5 imac 1.8GHz ppc with 1 gb ram. At first i just pressed enter on boot screen when loaded from Livecd. This got me into the ubunto livecd system but my wireless mouse and keyboard didnt work.

I read a post on this forum about pressing F6 and the adding single parameter but this failed to load the livecd. Now i cannot even get into the livecd - it says microcode5 bcm43xx not available or failed to load.

I have tried starting in nosplash and live, and liveppc64 to no avail. Any help will be greatly appreciated. I want to run ubuntu alongside OSX panther eventually but want to try out ubuntu via the live cd first.

---

