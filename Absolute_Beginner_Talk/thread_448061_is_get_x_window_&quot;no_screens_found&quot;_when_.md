---
title: "is get x window &quot;no screens found&quot; when trying to install ubuntu"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by oxymoronic on 2007-05-18
Edit, I've just seen the sticky, please forgive me :(
Hello :) I'm trying to install ubuntu 7.04 on my dell insperon I6400 laptop. It uses the ATI mobility radeon x1300. I really dont know what to do. After the installation trys to start up x window i stops and asks if i want to see debugging info. When i say yes, all i get is  "no screens found". :( Can someone help?

---

### Post by lazyart on 2007-05-18
Once you get past the debugging info (there are two seperate logs you can look at) you'll be left at the textual login prompt.

Log in with the name and password you created.  Then type```
sudo dpkg-reconfigure xserver-xorg
```
When asked for what type of video card, select ati.  Accept the defaults on everything else. Once you get back to the prompt, restart your laptop and see if that gets you into the GUI

---

