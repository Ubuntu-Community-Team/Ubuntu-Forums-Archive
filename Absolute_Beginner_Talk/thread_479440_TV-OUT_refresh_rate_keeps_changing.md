---
title: "TV-OUT refresh rate keeps changing????"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-20
I used "sudo nvidia-settings" to set the dual view (to clarify: I am not using Twin View, but the second option called X-server or something) so I can watch net streaming files on my tv using s-video.  It works well but when I reboot the screen is sorta bigger than the LCD display I have.  I noticed that when I get back to Nvidia settings and change the refresh rate to AUTO than the screen fits, but I have to repeat this procedure every time I reboot which gets annoying.

By "not fitting" I mean that when I put the cursor on one screen side the screen scrolls to show the edge.  Its like the screen shows only about 80% while the rest is available through scrolling (cursor move).  I wonder whether this has to do with refresh rate of my TV (NTSC) being different than my LCD (60Hz)???

Thanx!!!

---

### Post by dannyboy79 on 2007-06-20
> **bagrol1 said:**
> I used "sudo nvidia-settings" to set the dual view (to clarify: I am not using Twin View, but the second option called X-server or something) so I can watch net streaming files on my tv using s-video.  It works well but when I reboot the screen is sorta bigger than the LCD display I have.  I noticed that when I get back to Nvidia settings and change the refresh rate to AUTO than the screen fits, but I have to repeat this procedure every time I reboot which gets annoying.

By "not fitting" I mean that when I put the cursor on one screen side the screen scrolls to show the edge.  Its like the screen shows only about 80% while the rest is available through scrolling (cursor move).  I wonder whether this has to do with refresh rate of my TV (NTSC) being different than my LCD (60Hz)???

Thanx!!!

instead of using auto, you need to find out what is correct and hard code it in your xorg.conf. you should be able to select different choices within nvidia-settings until you get to the one that does work when you chose auto, then just chose that one, also, are you making sure to save your xorg.conf after you change something in nvidia-settings?

---

