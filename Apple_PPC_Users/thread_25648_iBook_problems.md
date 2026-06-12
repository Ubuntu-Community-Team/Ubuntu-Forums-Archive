---
title: "iBook problems"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by Gray Ghost on 2005-04-10
When I boot off the LiveCD onto my iBook, I get a green screen that gradually fades into a white screen with lines, I tried to correct this problem by using live video=ofonly, but the problem still persists, any ideas?

---

### Post by Gray Ghost on 2005-04-10
I don't think the other problem is solved, but now it says that there is a problem with Xserver, or whatever (graphical display) and that I have to manually configure it myself, any help would be nice, I have yet to find help in the support documents.

---

### Post by joebolte on 2005-04-10
I think I have the same problem as this guy.  Here's my experience.

iBook 800 Dual USB
ATi Radeon Mobility 7500

Booting from the install CD - The default boot process brings up a the left side of the dialog window in the upper left corner.  There is another image of it in the lower left corner.  Booting with the video=ofonly parameter fixes this problem. The install procedure goes noramlly from this point.  I eject the cd and restart.  Boot stage 2 takes over and starts installing packages like crazy. When I come back from a sandwich, the screen has 1-5 thin horizontal lines and a background which brightens and eventually dims. When it's bright it looks like a picture of stars and gas clouds.  No keys do anything at this point, except for apple-ctrl-power to hard restart. The restart brings the same result, shortly after the text mode report indicates that GDM has loaded. 

It seems pretty clear to me that it's a graphics problem, since all the text stuff works fine. I can boot fine in single-user mode using "Linux 1" at the yaboot prompt.  The /etc/X11/xorg.conf file lists the card as a Radeon 9000, which is incorrect.  Can someone who has a working hoary install and a Radeon 7500 post the contents of their xorg.conf? it would be especially helpful if you have an iBook.

Thanks,
Joe

---

