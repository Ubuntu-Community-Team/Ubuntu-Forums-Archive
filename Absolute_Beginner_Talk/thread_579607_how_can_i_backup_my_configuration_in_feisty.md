---
title: "how can i backup my configuration in feisty"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by tonym53 on 2007-10-18
I have spent ages getting feisty to work with 3d desktop
how can i make a configuration backup will i lose all thes settings if i upgrade to gutsy gibbon?

---

### Post by jackflap on 2007-10-18
I don't have any ideas on how to migrate your 3d settings over. I'd bet that you might have to reconfigure it from scratch.

Maybe back-up before you do though.

Look into SystemRescuCd ([http://www.sysresccd.org/System-tools](http://www.sysresccd.org/System-tools)) which is a Live Linux CD with all system utilities required to maintaining, rescuing, repairing, and recovering your system.

So, I would think somthing like the following: Download the image, burn it to a cd, and boot into it, then use the Partimage application to create an image of your system on a network drive, or on another hard-drive, maybe even on the same hard-drive (not sure if this will work). And if you mess up your system, then just restore the image of your drive to get all your settings back.

Another solution, one which I'm going to follow personally, is to install Gutsy fresh alongside my Feisty installation, get everything configured and working in due time, and then when everything's ready, wipe my Feisty install.

Let us know how it goes.

Alex

---

