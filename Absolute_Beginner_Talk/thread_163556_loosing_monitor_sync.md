---
title: "loosing monitor sync"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-04-21
When I boot Ubuntu the monitor sync starts out fine, but when I get to just before the login screen the monitor looses sync for about 5 seconds before going back into sync.   I can then login and proceed to run ubuntu normally.  Any idea's........

alienexplorers

---

### Post by dermotti on 2006-04-21
Hmmm, you could always backup your /etc/X11/xorg.conf and run **sudo dpkg-reconfigure xserver-xorg**

When you get to the section about setting up your monitor, use the **simple** technique. This will rule out any wack setting you have in your existing xorg.conf

---

### Post by alienexplorers on 2006-04-21
Tried that and problem is still occuring.  Any other idea's??????

alienexplorers

---

