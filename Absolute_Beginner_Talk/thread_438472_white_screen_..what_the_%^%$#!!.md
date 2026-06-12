---
title: "white screen ..what the %^%$#!!"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-05-09
Initially when I installed Ubuntu I could only get 800x600 resolution so I enabled NVIDIA restricted driver (something) I can't remember what it is called so I could use 1024x768. A few minutes ago I turned off the NVIDIA restricted driver...don't ask me why,#-o  and now when I log on all I get is a white screen and have no idea how to resolve this snafu I created:oops: . Iam looking at a white screen and don't know what to do to restore my desktop background. I can move the mouse pointer but what keys do I press to get me back to the point where I can view my desktop again.  
Help[-o<

---

### Post by starcraft.man on 2007-05-09
> **smoaky said:**
> Initially when I installed Ubuntu I could only get 800x600 resolution so I enabled NVIDIA restricted driver (something) I can't remember what it is called so I could use 1024x768. A few minutes ago I turned off the NVIDIA restricted driver...don't ask me why,#-o  and now when I log on all I get is a white screen and have no idea how to resolve this snafu I created:oops: . Iam looking at a white screen and don't know what to do to restore my desktop background. I can move the mouse pointer but what keys do I press to get me back to the point where I can view my desktop again.  
Help[-o<

Ummm, I assume that you booted up regularly. Did you try to boot into safe mode? You should be capable of that, if so then just open up the terminal and type in this:

sudo gedit /etc/X11/xorg.conf

Then scroll down the file until you find the entry thats your graphics card, then change the entry next to driver from "nvidia" to "nv".

After that reboot into your computer and well, we shall have to figure what made it go white screen. >.>

---

