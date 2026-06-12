---
title: "[SOLVED] accidentally removed network icon - cannot find it in the list..."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by KaYnemO on 2007-09-18
this will sound stupid, but i have been using kde for a few years and a total noob in gnome. in the top panel i had a great icon for network that, when the network module was activated, like wifi, would allow me to join the network without opening extra windows by simply clicking the right mouse button. it is gone after i have accidentally removed the notification applet. i returned the notification applet and got the power management icon back, but the network icon is gone, alas. other network applets that are available for an addition to the panel are different in usage (actually there is just one), any help???

---

### Post by mocoloco on 2007-09-18
Yeah, the one you can add by right-clicking is the old one, Network Monitor.  You want the Network Manager app, which for some reason you can't add by right-clicking the panel.  To run it on startup open System -> Preferences -> Sessions.  If you have a line in there for "Network Manager" make sure it's checked.  If not, add one.  The command is "nm-applet --sm-disable".  
Now it should show after your next login.  You can also run that using Alt+F2 to start it without logging out.

Edit: Duh on me, you can't add it through right-click because it's not actually a panel applet, it runs in the tray (notification area).

---

### Post by splintercellguy on 2007-09-18
Perhaps you need to re-add the notification area?

---

### Post by KaYnemO on 2007-09-22
thanx guys! i fugured it out! it's great!

---

