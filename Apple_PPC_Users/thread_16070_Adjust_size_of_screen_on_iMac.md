---
title: "Adjust size of screen on iMac"
date: 2005-02-19
forum: Apple PPC Users
---

### Post by Zundfolge on 2005-02-19
I just installed Ubuntu on a little iMac we had lying around at work. Only problem I've had is that there is no way to adjust the horizontal or vertical size of the image on screen and the bottom panel is off the screen.

Unlike most monitors which have buttons on the monitor itself to adjust such things, I can find no way via software to make these adjustments.


Any idea how I can fix this?


on a side note, this Mac has a single button mouse ... under MacOS you hold down control and click to get the "right click" ... how do I do this under Ubuntu?

---

### Post by patrickallo on 2005-02-19
Changing the size of the screen can be done with xvidtune


ctrl-click is obtained with F12


both work on my bondi-blue iMac

---

### Post by spaceballl on 2005-02-21
Thanks for the xvidtune info! That solved my exact same problem with my G3 500 iMac.
-Kevin

---

### Post by gunug on 2005-02-25
Anyone know how to do the same with a G4 hooked to an old MAC monitor (It's currently set for 1024x768).  I'm assuming from past Linux experience that there is some xconfig tool or something!

---

### Post by barneylaughs on 2005-08-09
i'm having what sounds like a similar problem. i have an imac g3 233mhz bondi, and after installing ubuntu, the screen resolution is horrible. i think it's 512x384 or something like that.

i tried using xvidtune to make it better, but it didn't do any good. i know i read something a while back about editing the xorg.conf file and changing the horizontal sync setting from "60-60" to just "60" but that didn't work this time. i got it working a while ago, but now i forget what i did. i think i added something to the .conf file about a default resolution... maybe?

apparently this particular imac is very picky about having the specific settings for it to display at a normal resolution like 800x600. anyone got any ideas? i've been googling for several hours now.

---

### Post by jRin on 2006-01-02
Hi, 

Thank you very much telling about xvidtune, solved my problem. :)

I had exactly the same problem barneylaughs. It solved when I changed in "/etc/X11/xorg.conf"  "DefaultDepth" -value from "24" -> "16". Just that change and reboot changed resolution automatically to 1024*768@75Hz.  (And "screen resolution" doesn't even offer anything else.... doesn't matter :) )

Hope that someone founds this useful (and sorry about gravedigging old thread), but thanks again about the xvidtune... 

-jRin

---

### Post by chs007 on 2006-01-10
I ran xvidtune in an xterm but don't see a way to change resolution. Also I have modified the xorg.conf file as suggested above, then rebooted and my G3 is still stuck at 640X480.

Any other suggestions?

Thank you!

---

### Post by barneylaughs on 2006-03-02
jRin: Thanks a TON! I had given up on Ubuntu when I couldn't figure this out like 6 months ago, and switched to Yellow Dog Linux. I actually like Yellow Dog better, but recently I installed Ubuntu again, and now your tip came in handy!
Thanks!

---

