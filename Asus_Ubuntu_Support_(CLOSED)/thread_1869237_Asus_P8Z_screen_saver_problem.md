---
title: "Asus P8Z screen saver problem"
date: 2011-10-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Bagbug on 2011-10-25
Hi,

since yesterday, when ever Ubuntu (10.04 LTS) goes on the screen saver (blank screen) there is no way I can make it come back to the desktop. The screen stays blank. I only see the mouse.

I can reboot from ssh connection from another computer and Zimbra is working fine.

Any idea ?

tx

---

### Post by 2F4U on 2011-10-25
Did you look into the log files? /var/log/Xorg.0.log and .xsession_errors probably would be most relevant.

---

### Post by Bagbug on 2011-10-25
> **2F4U said:**
> Did you look into the log files? /var/log/Xorg.0.log and .xsession_errors probably would be most relevant.

hi and where can I find the .xsession_errors file ?

And btw, I dont have the problem if I disbale the "Lock screen when screensaver is active" but I have it if I manually lock the session using the upper right button in the menu.

tx

---

