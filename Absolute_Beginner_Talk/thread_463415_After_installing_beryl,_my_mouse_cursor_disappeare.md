---
title: "After installing beryl, my mouse cursor disappeared"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by dacookiemonn on 2007-06-03
Im beginning to think that installing anything in linux is like taking a pill with unknown side effects.  Is there not one thing that goes standard here?
Anyways, I had to reinstall ubuntu 7.04 last night again because I used a nvidia driver, where apperantly it was not needed and it brok the whole gui.
Well I installed beryl and it went fine.  As soon as I start it up, my gui is all white adn unoperable.  I log out and into safe terminal and restore a backup xorg config and the gui is back working, but I can not get the mouse cursor to show.  It is there, I just dont see it.
Can anyone suggest a starting point, also maybe some help on if I need to get a different nvidia driver.  I got a 6150 go and ubuntu says I dont need the restriced hardware driver.  Thats where I messed up last night.  I did this on my desktop becasue It allowed me to and said I needed to activated the nvidia driver and BAM, beryl and everything worked on desktop.  Laptop is different story.  Any help?

Thanks

---

### Post by dacookiemonn on 2007-06-03
I still dont seem to get it working

---

### Post by dacookiemonn on 2007-06-03
I found it, just so other reading this thread will have an answer for future refernce.
I had to add in the screen section under bit depth, the following option:

Option   "HWCursor"  "off"

My cursor cam back, now for figuring which nvidia driver or method to install beryl on the laptop.

---

