---
title: "[SOLVED] If xorg-conf doesn't exist - whats up?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-07-15
Hi,
"sudo nano /etc/x11/xorg.conf" gives me a result that it doesn't exist. Therefore I cannot change anything.
I looked at the other posts and have tried all suggestions to ammend` the xorg.conf file.
I'm using restricted drivers for my nvidia 7600 GT and I cannot get the screen resolution to stay.
When I'm in nvidia control centre I save to file 1650x1050 (16:10)- hopefully xorg - unfortunately at next boot the screen resolution has returned back to the default of 1024x768.
If the xorg file doesn't exist - what do I know - I cannot alter the refernece to allow a default screen of even 1440X900 to suit the viewsonic - but the 1650x1050 would be better.

Any suggestions on how to resolve the missing xorg file appreciated - or where am I going wrong.

Best Regards
Bill

---

### Post by Nythain on 2007-07-15
capitol X like this
/etc/X11/xorg.conf
linux is very case sensitive

---

### Post by RedSquirrel on 2007-07-15
The file is /etc/X11/xorg.conf (that's an uppercase X). ;)

EDIT: Darn. You beat me by a few secs Nythain. :)

---

### Post by wapfu on 2007-07-15
Cheers Guys.
Case sensitivity - ta.
Best Regards
Bill

---

