---
title: "HELP installing"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by thornton2003 on 2007-10-24
I can't install Ubuntu.  I can get into the install screens but I can't see the very bottom of the screen to press forward.  I've tried switching monitors with no luck.  I've tried to resize the window no luck.  The window doesn't minimize so that doesn't work.  I thought maybe it had something to do with an incorrect driver.  I installed XP with no problems updated the all the drivers set the screen to 1152 x 864 pixels.  Found instructions to do a dual boot.  Popped in the Ubuntu install disk and BAM the screen went large on me again so I can't see the bottom quater of the window.  The mouse goes past my viewing capabilities because I used some screen shots of where the forward button should be and blindly clicked to advance to the next screen. 

Any suggestions?

---

### Post by mikeyphi on 2007-10-24
If you're using the LiveCD try setting the screen resolution under System/Preferences.

Another option is to install Ubuntu using the 'Alternate' CD - this uses a text-based installer so might not cause a screen problem.

In either case you should probably do some research about support for your specific Graphics card.

---

### Post by molly_001 on 2007-10-24
> **thornton2003 said:**
> thornton2003 wrote . . . 

I can get into the install screens but I can't see the very bottom of the screen to press forward. 



The problem you described is with the x-server, which handles your graphics adapter and further, handles xorg, which is your window manager for Ubuntu desktop.

Google the following phrase " sudo dpkg-reconfigure xserver-xorg " and you will soon have that fixed.  (I would go with default 1024x768 VESA configuration.)


[quote=thornton2003]I thought maybe it had something to do with an incorrect driver.  I installed XP with no problems updated the all the drivers set the screen to 1152 x 864 pixels.  Found instructions to do a dual boot.  [/quote]

The drivers for Windows XP, or any part of Windows XP, would have nothing to do with how Ubuntu is configured.  Keep in mind that we can help much more if you can report back your graphics adapter (graphics card) type or name of card.

---

