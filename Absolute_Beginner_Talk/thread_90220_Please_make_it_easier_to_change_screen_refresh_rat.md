---
title: "Please make it easier to change screen refresh rate"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by bobkoure on 2005-11-14
There are a lot of CRT monitors still out there and 60Hz is downright painful for some of us.

After a half day of digging around I've figured out not only that I just need to edit /etc/X11/xorg.conf and change the [default monitor] refresh rates, that I need SU rights to edit this file - but that I don't actually need to set up a root account and password as the "run as another user" in the GUI expects *my* password (or possibly the password of the first user configured) rather than the root password when using "run as another user".

Then there's the whole issue of calculating horizontal refresh from vertical, and making sure I'd made a copy of xorg.conf before changing anything.

OK, fine, I figured it out. But I'm not at all new to computers (was even a "Unix guy" back in the mid 80's). How the heck is a newbie, either new to PCs or just fresh from Windows going to figure this out? Or are they just stuck with 60Hz - and come away with the impression that "Linux isn't very good - the monitor hurts my eyes"?

At a minimum, include a xorg.conf.vesa (or whatever - vesa comes to mind as 75Hz is the minimum recommended there), a simple command script to copy it over xorg.conf as su, and make sure the default monitor in the new file supports 75Hz.
Or maybe include a step-by-step somewhere here (or if there is one, make it easier to find - I'm not *that* bad at using search engines).

Oh - and "Hi Everybody! - sorry I had to make my first post here a grumble..."

Bob

---

### Post by earobinson on 2005-11-14
you should report this as a usibility but to bugzilla!

It would be nice if you could just force one and it would update the /etx/x11/xorg.conf file!

*extra points for searching to solve your problem instead of makeing a post*

---

### Post by Kyral on 2005-11-14
X usually calculates the refresh rates for you

---

### Post by Rizado on 2005-11-14
Yeah it usually does. At least on all the newer computers I've run with a live cd it have worked. But not on my PowerMac G4. (ATI Rage)

---

