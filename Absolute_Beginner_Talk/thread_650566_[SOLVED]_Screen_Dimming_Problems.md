---
title: "[SOLVED] Screen Dimming Problems"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by BandD on 2007-12-26
I installed Gutsy on my Vaio Notebook FS600 series a few months ago.  And the Gnome Power Manager had no problems dimming and un-dimming my screen when switching from AC to battery power or when I would move the brightness slider manually.  But then my hard drive died.  So I got a new one and reinstalled Gutsy.  Now I CAN'T dim the screen in any way.  

The oddest thing is that when I switch to battery power, the little brightness icon shows up on the screen displaying a diminished level, but the screen doesn't actually dim.  And likewise when I switch back to AC the brightness icon/meter pops up displaying full brightness.  But the LCD is always at 100%.  

Any ideas?

---

### Post by BandD on 2007-12-26
Very Strange...seems to be working now.  I wanted to check something in the BIOS (unrelated) so I had to restart, and upon restart (even though this machine has been restarted several times) dimming is fully functional.  I dunno...

---

### Post by BandD on 2007-12-31
Ok, so after a shutdown and then booting up the next day (today) the dimming doesn't work again.  I'm assuming that after a few restarts it'll work again.  It's a little annoying, but I can live.  If anyone has a recommendations, let me know!

Peace,

Dustin

---

### Post by BandD on 2008-01-01
After numerous restarts, log offs and the like, the screen just doesn't want to respond to the gnome power manager.  I can't figure out what it happening.  Gnome thinks it has control of the screen brightness, but it doesn't.  How can I get GPM back in control?!?!

---

### Post by BandD on 2008-01-02
So I've really been trying to figure this out, but I'm really just too much of a noob.  The dimming workins perfectly through the Live CD, so I thought, what the hey, I've got my Home folder backup on an external drive, I'll try a fresh reinstall of Gutsy.  But alas, once Gutsy is actually installed on on my system, g-p-m loses control of the LCD.  I know the issue is related to HAL in some way, but I just don't know enough about how g-p-m interfaces with HAl or who either of them work to even begin looking for an answer.  

It just seems strange to me that it worked before, and now it doesn't.  Can someone please just point me in the right direction.  Cause I don't really know where to start.

Thanks,

Dustin

---

### Post by BandD on 2008-01-02
Ok after a lot more searching I found these two threads:

[http://backports.ubuntuforums.com/showthread.php?p=3594699#post3594699](http://backports.ubuntuforums.com/showthread.php?p=3594699#post3594699)

and

[http://ubuntuforums.org/showthread.php?t=585745](http://ubuntuforums.org/showthread.php?t=585745)

I added   ```
value="`expr $value / 19235509`"
``` to the beginning of this script /usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux as stated in both of those posts.  

Don't forget root privileges!

Hopefully a fix will come soon!

---

### Post by Seeed on 2008-01-09
Thanks a lot!
This was the first solution for this problem that worked on my Sony Vaio VGN-N31M.

---

