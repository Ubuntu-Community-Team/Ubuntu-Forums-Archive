---
title: "Gnome log-out video problem"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Pete Watters on 2007-06-25
I'm not sure if this the best place to ask, but this is my first question to the user forums, and I *am* a relative newcomer to Ubuntu, so here goes...

I've installed the LAMP server version of Edgy Eft as a Parallels VM on an Intel MacBook Pro. In the menu.lst file, I've set the screen size to 800x600 (vga=0x314) and that works well. I then installed the Gnome desktop package, and have a video resolution of 1024x768x24 as set in the xorg.conf file with the "vesa" generic video driver. This works well, too. If I start Gnome via the startx command, I get a nice Gnome display at 1024x768. 

The problem I have is when I log out of Gnome or try to return to the console from Gnome by pressing Ctrl+Alt+F1. The screen doesn't return to 800x600, but gets garbled at 1024x768, forcing me to reboot to get back to the console. 

Any suggestions?

-- Pete

---

### Post by petedct on 2007-07-13
Hey Pete, I had a similar situation. My desktop would display nicely at the monitor’s 1440 X 900 native resolution, but the login screen would be displayed at something larger. I would have to move the cursor to the sides of the monitor to get the login window to scroll so I could see the options button or the time.
I edited xorg.conf so that the Modes line below Depth 24 only contained my desired resolution. See example below.

Depth 24
Modes "1440x900”

Now I have a nicely sized login window.

---

### Post by Pete Watters on 2007-07-16
Thanks for replying! My problem wasn't with the gnome desktop, but the command-line window when I logged off. I fixed the problem by changing the settings in the menu.lst file from 0x314 to 0x318, giving me the right size window at 24-bit depth. I just needed to keep the resolution the same on both windows.

---

