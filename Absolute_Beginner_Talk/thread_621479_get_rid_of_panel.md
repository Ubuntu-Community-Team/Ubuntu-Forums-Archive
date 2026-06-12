---
title: "get rid of panel"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-11-23
is there a simple way to get rid of the default panel in ubuntu? so there are no panels on the system?

thanks

(it seems you can remove panels when theres more than 1, but the last one doesn't have the remove option)

lets say I removed it, is there a way of getting back using the terminal, if I ever wanted too? other than using some other panel like fbpanel.

thanks so much

-saamon

---

### Post by markharding557 on 2007-11-23
don,t think you can remove the last panel
if want command line only then shut then shut xsever down

---

### Post by spiderbatdad on 2007-11-23
maybe. I'm assuming if you right click on the panel, the delete this panel option is grayed out?
I opened the gconf-editor by pressing Alt+f2 and input gconf-editor

when the editor opens go Apps->Panel->Global
then scroll down to see "Locked Down" with a box to the right. see if the box is uncheked.
Thats all I can suggest, and I'm not sure it's the right solution. I can delete all my panels.

---

### Post by Six_Digits on 2007-11-23
I don't know spider, this seems to simply remove all my options but "help" and "about" from a right-click on the panel...I'll look around some more.

---

### Post by Six_Digits on 2007-11-23
Lock Down Long Description - If true, the panel will not allow any changes to the configuration of the panel. Individual applets may need to be locked down separately however. The panel must be restarted for this to take effect.

---

