---
title: "HELP!! lost my panels can't get access to any thing!!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-25
i was trying to give my gnom desktop the attractive look as many guys doing so i followed a guide from [http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml](http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml) to change the look of my panels i installed AWN and i had to delete my both upper and lower panels but now all i got the desktop with my hard drivers and home folder on it :confused: now i can't access application or system or any thing i need help restoring my panels please

---

### Post by LowSky on 2008-03-25
type in terminal if you can get to terminal hit Alt and F2 at the same time

```
gnome-panel
```

---

### Post by angel_zone on 2008-03-25
> **LowSky said:**
> type in terminal if you can get to terminal hit Alt and F2 at the same time

```
gnome-panel
```

NEGATIVE!! nothing happened,somebody told me to hitCTRL+Alt+F1 but the screen become black and nothing happened:confused:

---

### Post by smurphy_it on 2008-03-25
Hit CTRL+ALT+F7 to get back to X-Windows.

If that doesn't work, you might have to reboot X-Windows... After hitting Ctrl-Alt-F7 and unsuccessful, try hitting Ctrl+alt+BckSpace

---

### Post by angel_zone on 2008-03-25
> **smurphy_it said:**
> Hit CTRL+ALT+F7 to get back to X-Windows.

If that doesn't work, you might have to reboot X-Windows... After hitting Ctrl-Alt-F7 and unsuccessful, try hitting Ctrl+alt+BckSpace
yes i know about CTRL+Alt+F7 and it worked but my proplem still there:confused:how to restore my panel????????? any help please i just hate to re-install ubuntu becouse of that reason:(

---

### Post by angel_zone on 2008-03-25
any one had idea abou starting the terminal CTRL+F2 didn't work any help please

---

### Post by angel_zone on 2008-03-25
COOM ON guys don't tell me i'll had to reinstall ubuntu becouse of the panel issue the first time installation was hard enough to think of reinstallation

---

### Post by smurphy_it on 2008-03-26
The problem isn't just the panels.  It's the fact that you can't get to a console to fix things.

I'm sure you could reboot and go into recovery mode.  Just not sure how to help you once there.

Hmm... Possibly adding Gnome-panels to a startup item.... Normally this would be sessions (if using Ubuntu).  

Hmmm... Just looking at my home folder, and wondering if you have this file, and what it says.

/home/%user_profile%/.gnome2/main

Replace %user_profile% with the name of your userid of course....

For example, here is the contents of mine.

[Placement]
Dock=LocationBar\\0,3,1,0\\ToolBar\\0,2,1,0\\MenuBar\\0,1,1,0

So you could paste that in, if the file didn't exist or if it is empty.

---

### Post by angel_zone on 2008-03-26
> **smurphy_it said:**
> The problem isn't just the panels.  It's the fact that you can't get to a console to fix things.

I'm sure you could reboot and go into recovery mode.  Just not sure how to help you once there.

Hmm... Possibly adding Gnome-panels to a startup item.... Normally this would be sessions (if using Ubuntu).  

Hmmm... Just looking at my home folder, and wondering if you have this file, and what it says.

/home/%user_profile%/.gnome2/main

Replace %user_profile% with the name of your userid of course....

For example, here is the contents of mine.

[Placement]
Dock=LocationBar\\0,3,1,0\\ToolBar\\0,2,1,0\\MenuBar\\0,1,1,0

So you could paste that in, if the file didn't exist or if it is empty.

sorry i'm taking so long to replay as i'm "jumpping"between ubuntu and windows to use the web!! any way i found that folder home/user/main and it was just as you wrote but i wonder about using the recovery mode will it works any body helps me with this please (actually experinced one)

---

### Post by angry_johnnie on 2008-03-26
Well, you can see your hard drives on the desktop, right?
Why don't you open one.
Once you have a nautilus window, try to acces the following directory

/usr/bin/

and look for gnome-terminal

double click on it to launch it.  And then type

```
gnome-panel & disown
```

---

