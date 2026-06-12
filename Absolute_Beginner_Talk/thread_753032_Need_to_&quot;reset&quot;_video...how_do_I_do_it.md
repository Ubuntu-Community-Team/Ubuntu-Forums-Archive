---
title: "Need to &quot;reset&quot; video...how do I do it?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by xdibblerx on 2008-04-12
I have an ATI X1300 Pro card and I went through the procedure to install the Ubuntu drivers from the guide at cchtml.com.  This was done on a Hardy install but I figure my problem is fairly universal.

I was getting some flicker when I ran some games using the ATI drivers and so I went into the "Graphic and Screen settings" and changed the driver to ATI and the type to Radeon.  The test looked fine so I accepted and everything was fine till I rebooted and all I got was a white screen after I logged in.  After some panic I ended up switching the monitor to the onboard video and managed to get into Ubuntu to try and reset everything back to "factory fresh".  I did manage to get the ATI card working again but with some major glitches and a max resolution of 800x600.

Is there an easy way to reset Ubuntu back to the way it was at installation or a way to reset the video?

---

### Post by Hospadar on 2008-04-12
well the thing to do, is to backup your /etc/xorg.conf file before you do any modifications, then if you don't like what happened, you can just drop the backup back in place.

Seeing as you didn't know this before you started, you'll have to go the alternate route, in a terminal type "sudo dpkg-reconfigure xserver-xorg" on the very first page, select one of the open source drivers, probably vesa.  There is an open source ati driver also (which doesn't provide 3d accelleration, so you probably won't notice the diff between it and vesa) but I forget what it's called, so if you figure out, you could use that too.  Then hit enter a bunch of times, selecting the default options.  You'll eventually get to a screen asking about resolutions, use spacebar to select the maximum resolution you'd like. then default your way through the rest of the dialog

You'll have to restart the x server after your changes, either Ctrl-Alt-Backspace, or in a terminal, type "sudo /etc/init.d/gdm restart"

---

