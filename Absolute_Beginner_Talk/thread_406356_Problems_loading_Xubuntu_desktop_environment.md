---
title: "Problems loading Xubuntu desktop environment"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by magustrate on 2007-04-10
I'm reasonably new to Xubuntu and I've been having some problems with my install as of late. I wasn't having any problems until recently. I'm not sure exactly what I did but I restarted my computer (a 800mhz G3 iBook running Ubuntu 6.06 with the Xubuntu desktop) and now when I log in instead of going to the desktop there is only a blue screen. From here I can use Alt-F2 or Alt-F4 to bring up Run program or help but I don't get a desktop environment. 

What can I do so that when I log in I get my desktop? What questions do you need answered to help me? I've tried searching the forums but haven't found anything.

---

### Post by aidanr on 2007-04-10
hit alt+f2 and type in xfdesktop

---

### Post by magustrate on 2007-04-10
When I do that it brings me to the desktop but my toolbars at the top and bottom are missing. It also will not let me quit when I use the button at the bottom of the menu when I right click.

---

### Post by aidanr on 2007-04-10
make sure xfce4-session and xfce4-panel are running (again, same way alt+f2)

---

### Post by magustrate on 2007-04-10
Alright, I have ran both xfdesktop and xfce4-panel and I have my desktop up and running but I can't quit out to the log in screen, shut down or restart. According to my task manager xfce4-session is running, but even if I run it again I don't get any response to this. Any further suggestions?

---

### Post by magustrate on 2007-04-10
When I try to log out/restart/ shut down I get this reponse:

"Quitting the session requires that Xfce's session manager (xfce4-session) is running, but it was not detected.  Please quit Xfce via another means." 

But it is clearly listed in the task manager.

---

### Post by aidanr on 2007-04-11
well just came across a tip that might be worth trying, clear out ~/.cache/sessions and reboot from the terminal (sudo reboot)

---

