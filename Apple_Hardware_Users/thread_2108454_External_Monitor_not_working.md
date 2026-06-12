---
title: "External Monitor not working"
date: 2013-01-24
forum: Apple Hardware Users
---

### Post by TovrikTheThird on 2013-01-24
I have a MacBook Pro 5,5 (mid-2009) and am running Ubuntu 12.04 LTS. I just installed it a few days ago and therefore haven't done any tweaking of the operating system. When I plug in my external monitor via mini-display port, there seems to be no recognition of the screen. I know there isn't a physical problem with the screen or cable, because it works with OSX. 

Measures I have taken:
Installed addition drivers via the additional drivers app
Checked System Settings > Displays and tried detecting display and nothing happens

Has anyone run in to this error, and is there a known solution?

---

### Post by TovrikTheThird on 2013-01-28
OK. I figured it out. I had to go into an application called NVIDIA X Server Settings. Then you click on the menu marked "X Server Display Configuration." In there you click Detect Displays and set the external monitor to TwinView. Then click apply.

---

