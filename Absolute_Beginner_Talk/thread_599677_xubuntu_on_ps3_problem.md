---
title: "xubuntu on ps3 problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by vagrant_xii on 2007-11-01
I'm having trouble trying to change the resolution on xubuntu on my ps3.  My ps3 is hooked up to my hdtv via hdmi.  When i try to select resolutions in display preferences none is shown.  I have tried using that ps3videomode -v ## in the terminal but doesn't really work.  Can someone help me out?

---

### Post by jrstmartin on 2008-02-27
Forget messing with resolutions in xorg.conf.  I was trying to display 1920x1080 on my Song KDLXBR40 in 1080p.  Using mode 5 for 1080p left an area of black unused screen around the displayed GUI.  Switching to all the different resolutions in xorg.conf did not make use of the unused space, it just resized the GUI in the area being used.  This really pissed me off for a while, as I have this great TV and couldn't even make use of the entire screen...

Solution - Use Full Screen mode by adding 128 to the video mode that you have chosen.  So for me, for 1080p utilizing the entire screen, "mode:133".  Done.

Also instead of changing resolutions in xorg.conf, you could just change to a different video mode, so for me, I could drop down to 720p (720p is mode:3) "mode:131" if I wanted a larger GUI, similar in size to 1024x768.

If you have no idea how to change your video mode go here, scroll to Video Modes:

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

---

