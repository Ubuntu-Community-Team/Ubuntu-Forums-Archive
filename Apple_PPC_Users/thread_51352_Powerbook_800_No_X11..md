---
title: "Powerbook 800 No X11."
date: 2005-07-23
forum: Apple PPC Users
---

### Post by John Kiniston on 2005-07-23
Howdy,

I just insalled Ubuntu on my Powerbook 800 and I've run into a major snag, No working X11.

When the system boots I get the normal text based init process, then the screen goes black and the light seems to turn off, Finally I get a screen with white bars that seem to grow/spread and at that point I generally panic and hold the power button until the system turns off.

I blew away my working copy of 10.4 on this system when I installed so I cant even go back to it until I go back to work on Monday to see what resolution I need.

Does anyone have a Powerbook 800 with working X11?

---

### Post by dasaivet on 2005-07-24
Hi, that's strange
I had a similar problem with screen resolution and dual monitor...try

sudo dpkg-reconfigure xserver-xorg

or modify your xorg.conf file manually

Cheers

---

