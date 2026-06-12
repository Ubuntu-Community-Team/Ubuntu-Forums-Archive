---
title: "synaptic read only"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by rjgould9r on 2007-03-07
Hi 

I'm pretty new at linux and Ubuntu. When I try to get into synaptic from the drop down menu, It tells me I am not root so it will open as read only. If I try to use the command line, I get an error  Gtk-WARNING **: cannot open display: . I can get it to work with alt-F2 synaptic. I did a reinstall. I did aptitude update and aptitude upgrade but I still get the window telling me synaptic will open as read only. Any ideas?:confused:

Rich

---

### Post by BgPup on 2007-03-07
This is something of a shot in the dark, but have you tried opening the menu editor and looking at the properties of the menu item?  I haven't messed with these since Dapper, but the 'command' property for the synaptic menu item should be "gksu synaptic" I believe.  Is this the case?

---

### Post by rjgould9r on 2007-03-07
Worked like a charm!! What do the letters mean? the command had /usr/sbin/synaptic in it. Thats where the exe file is loacated.

How do you guys remember all this stuff?

Thanks for the help.

---

### Post by Kateikyoushi on 2007-03-07
Have to use that regularly so it would be hard to forget.
What the gksu or su does is explained over here. [LINK]("https://help.ubuntu.com/community/RootSudo")

---

