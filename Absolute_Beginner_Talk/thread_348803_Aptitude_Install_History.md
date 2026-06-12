---
title: "Aptitude Install History"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-01-29
When I install with Synaptic Package Manager, Add / Remove, or Update, I can find the history in Synaptic under File--->History. Is there a history file for "sudo aptitude install"?

---

### Post by someusernoob on 2007-01-29
Open a terminal and copy/paste:
cat /var/log/aptitude >> /home/`whoami`/Desktop/aptitude.log

Then the whole log should appear on your desktop and you can open it with gedit. You can throw it away anytime, it is only a copy.

Or you can just copy/paste this into a terminal:
cat /var/log/aptitude

But you might not see the whole log if you set your terminal to e.g. 500 lines of output (if the log file has more lines, which it often does).

Or you can navigate manually with the Nautilus filebrowser to /var/log and open the aptitude log by double clicking it.

Hope you learned something from it :)

---

### Post by Stunt Double on 2007-01-29
Thank You.
Now I can see which dependencies were installed.

---

