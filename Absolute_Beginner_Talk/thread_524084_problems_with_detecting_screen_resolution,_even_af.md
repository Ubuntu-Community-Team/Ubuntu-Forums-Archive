---
title: "problems with detecting screen resolution, even after the xserver config"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by scott pruett on 2007-08-12
I have a fresh install on an Alienware Sentia m3450, and I can't get its native screen resolution to function.  I ran the 'sudo dpkg-reconfigure xserver-org' script, selected the max resolution & everything lower, restarted the xserver, re-logged in, still no dice.  I re-ran the reconfigure xserver thing twice more & the resolutions I initially selected were still set in the script w/in the terminal, but the main preferences still only show 1024x768, 800x600, 640x480.  

The chipset is a Mobile Intel 945GM Express.  Resolution is 1280x768.

Any ideas? 

thanks!

---

### Post by yorkie on 2007-08-12
[http://ubuntuforums.org/showthread.php?t=454328&highlight=Mobile+Intel+945GM](http://ubuntuforums.org/showthread.php?t=454328&highlight=Mobile+Intel+945GM)
read this thread scroll down to Atomic dog answer this seems to be what you want

---

### Post by scott pruett on 2007-08-12
thanks yorkie... i removed the i810 driver, but unfortunately that didn't do the trick.

I reposted this in the hardware & laptops section; please continue discussion in the following thread, as I'm now getting responses in both (oops):

[http://ubuntuforums.org/showthread.php?t=524155](http://ubuntuforums.org/showthread.php?t=524155)

---

