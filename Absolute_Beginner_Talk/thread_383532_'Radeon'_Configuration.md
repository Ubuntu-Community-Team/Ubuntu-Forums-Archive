---
title: "'Radeon' Configuration?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by NuklearToaster on 2007-03-13
Is there any way to edit the current configuration used by the driver 'radeon'? I'm having problems using it with my Radeon9000. I've managed to get fglrx to identify properly, but I'm trying to get Beryl to work, with both XGL and AIGLX configuring either my drivers or my xorg to a point that it no longer recognizes my card!

If that made little to no sense, trust me, I understand. Linux makes about as much, if not less, sense to me, but I have really got to get away from windows. My problem, in the long run, is that I can get fglrx to verify that my video card (It's taken 2 weeks just to get it to that point, mind you), but when I try to boot into AIGLX or a XGL session (for Beryl), it tells me that I have no manageable screens. However, if I use the 'radeon' driver, XGL lags down, AIGLX will -not- load, the login screen is too large for my screen, which causes it to break on some occasions. (Such as, I have to scroll down to find the 'Options' button, which sometimes causes all hell to break lose and the screen to either cut off or jumble everything beyond recognition.)

I see plenty of way to setup the fglrx drivers... Now is there a tutorial for setting up radeon drivers?

---

### Post by Oen386 on 2007-03-13
I did a fresh install, then I ran the script by "Waappu". Do a search on these forums for it.

It will install the necessary items (including Beryl and ATI drivers). Once that is finished go to the very last page in the post and you will see something about Xorg 7.2 drivers. Once I installed that also.. presto. Everything worked great (except for different backgrounds for different sides of the cube).

Good luck.

---

### Post by NuklearToaster on 2007-03-13
Well, this is off a pretty fresh install (yesterday morning, I've ran the AIGLX + ATi auto script, the Envy script, and tried to XGL it, but to no avail.) so I guess it is worth a try. Thank you! :)

---

