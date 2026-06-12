---
title: "Macbook resolution and graphics problem"
date: 2008-10-06
forum: Apple Hardware Users
---

### Post by ricky0319 on 2008-10-06
I configured my etc/X11/xorg.conf file. I realize now i should have been more careful. Now my display and graphics card is not recognized. I tried to default to the old xorg.conf file, but this didn't work. I can get my screen resolution to 1024x768, but it will not work at 1280X800. I have tried to change the display, but 1024x768 is the highest resolution I can get to. I am using a macbook with hardy heron. Is there some default xorg.conf file I can use?

---

### Post by cyberdork33 on 2008-10-06
> **ricky0319 said:**
> Is there some default xorg.conf file I can use?
run ```
sudo dkpg-reconfigure -phigh xserver-xorg
```

---

### Post by ricky0319 on 2008-10-06
I have tried this and did not work. I ctrl alt Backspace to restart too.

---

### Post by cyberdork33 on 2008-10-06
can you post your xorg.conf? You can also check the xorg logfile for error messages. It is in /var/log/Xorg.0.log

---

