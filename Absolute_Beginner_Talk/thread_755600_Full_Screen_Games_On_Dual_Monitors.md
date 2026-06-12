---
title: "Full Screen Games On Dual Monitors"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by myst1c on 2008-04-15
i have dual monitors, and whenever i try to play any games that would normally take up the full screen, they just go halfway off of one screen... is there a simple way to remedy this? or do you need more information? and if you do, what information do you need?

---

### Post by OliW on 2008-04-15
Yes, you need to switch the order of your monitors.

I assume you're using twinview on nvidia. Load up nvidia-settings (as root), and go to X Server Display Configuration. Select the left screen and click the "Make this the primary display for the X screen.

Now, you'll have to move your panels about and the login screen will move to the new default - but games will work.

---

