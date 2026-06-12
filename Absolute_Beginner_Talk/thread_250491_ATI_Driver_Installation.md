---
title: "ATI Driver Installation"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Penzao on 2006-09-04
Hey i have a Radion X600 and i really have no idea as to where to start with the drivers. Earlier my GUI wouldent start so i has to do the sudo dpkg-reconfigure xserver-xorg and select the vesa drivers. Now i am wondering how to install the proper ATI driver for my card.

I am a total newbiw though and have no idea what OpenGL or anyof this is. Thanks for the help!

---

### Post by Anonii on 2006-09-04
I'd recommend following the instructions in this thread:
_[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)_

It enabled OpenGL support and direct rendering in my x600 card, when any other howto wouldnt.

Good luck and please, post your results.

---

### Post by trebor on 2006-09-04
> **Anonii said:**
> I'd recommend following the instructions in this thread:
_[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)_

It enabled OpenGL support and direct rendering in my x600 card, when any other howto wouldnt.

Good luck and please, post your results.

I have just gottne done doing this how to.  When I first started back up it siad my graphic server was not working.  so I reinstalled the driver with gnome not loaded up. then I restarted and all was good.  It seems that the step to remove the old driver should be before you install the new as it seems to unistall both at once.

---

