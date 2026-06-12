---
title: "Mac pro ubuntu restart fails"
date: 2018-10-25
forum: Apple Hardware Users
---

### Post by urmajest on 2018-10-25
I have installed ubuntu desktop (originally 14.04 and now 18.04) on my Mac pro (Late 2013, black trash can model).

I basically followed the guide in the following document:

[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

In short, I have installed rEFInd and then ubuntu desktop with grub.

The problem is that [B]restarting ubuntu usually fails.
[/B]
Please let me describe further.
[LIST=1]
[*]How does it fail? It appears everything is normal until it sounds the chime; the machine shuts down and reboot to play the chime sound but the screen shows a blinking folder icon with a question mark inside. If I hold the power button to force shutdown and press the power button again to boot, the booting sequence goes normal. As long as I'm not rebooting, the booting sequence goes normal.
[*]When does it fail? If I issue "sudo reboot", it always fails. If I issue restart by GUI (hit the power icon on the top right corner of the desktop and choose restart), it normally fails but sometimes it does not.
[/LIST]

I don't figure out where to start debugging this problem. Can someone please suggest some solution?

---

