---
title: "Log in failure after installing updates, parallels, intel imac"
date: 2007-03-21
forum: Apple Intel Users
---

### Post by ranmasaotome on 2007-03-21
Launched today after a few weeks of not using, had to register and update parallels, was able to do so without incident. Many updates to install within Ubuntu, downloaded and installed updates automatically, restarted, no-longer able to log in. If I type in the wrong username and password I do get the appropriate error, but if I type in the correct username and password, I very briefly see a text screen which I am unable to pause on, and then I get the login screen again and a drumroll. If I restart I can go into "recovery" mode but I have no idea what to do there.

---

### Post by cyberdork33 on 2007-03-21
sounds like Xorg is crashing, and it automatically restarts...

you can get to a terminal by doing CTRL+ALT+F1 or F2, etc.

You can then check your xorg.conf and Xorg logs for errors

---

