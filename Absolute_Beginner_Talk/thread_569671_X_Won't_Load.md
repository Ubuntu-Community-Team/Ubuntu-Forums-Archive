---
title: "X Won't Load"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Lee_Lee87 on 2007-10-07
Well, I've just done a fresh install on a new system. Everything was up and running fine till, I tried to install some nvidia drivers. I've tried a few things but nothing seems to work. I just tried this 
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html]("http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html") and now X won't load. Grub loads up then ubuntu load screen, after its loaded my screen just goes black.
If I hit enter it shows a failure to load x message and asks if I wish to view the logs. After this I am unable to get back to a command prompt or do anything else. So anyone have any ideas on how to fix this? 
Also whats the best way to install the latest nvidia drivers? I already tried envy but had no luck. If it helps I have a 8600gts.

---

### Post by phidia on 2007-10-07
To open up another instance of the CGI (often called a tty) just press the Alt+Ctrl+F1 keys.
Login and then type  "sudo dpkg-reconfigure xserver-xorg" (without the quotations marks) press the enter key and run through the x setup program.
To install the proprietary Nvidia driver check out the multimedia and video section for that driver how to, or use [this]("http://ubuntuforums.org/showthread.php?t=301499").

---

