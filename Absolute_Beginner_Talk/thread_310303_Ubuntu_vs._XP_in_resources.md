---
title: "Ubuntu vs. XP in resources"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by johnmxg12 on 2006-12-01
Hey guys i'm relatively new to Ubuntu, and i was wondering if there was a program for Ubuntu that shows the computer's resource allocation.  i want to monitor the programs that are currently running and make sure i'm not running my laptop to the limit.  

and i also had another question, which OS (xp or Ubuntu) uses up more resources?

---

### Post by johnmxg12 on 2006-12-01
that program i'm thinking about is an equivalent to task manager in XP.

---

### Post by aysiu on 2006-12-01
Press Alt-F2 and type ```
gnome-system-monitor
``` There's probably a keyboard shortcut for this as well, but I can't think of it off the top of my head.

---

### Post by 23meg on 2006-12-01
System Monitor in the default installation may be what you're looking for; you can find it in System / Administration / System Monitor.
> and i also had another question, which OS (xp or Ubuntu) uses up more resources?You'll get varied answers for different use cases. With a light desktop environment such as XFCE and / or some tweaking, you can surely go below the XP average, but the two systems have very different ways of handling resources, so it's hard to tell by looking at figures. Linux will allocate free memory for caching very aggressively, for example.

---

### Post by Cynical on 2006-12-01
No its easy to tell using system monitor. Upon install Ubuntu will use around 60-100mb of memory. Windows XP uses around 300mb. The thing is in linux memory handling is very efficient, it uses almost all of your memory for caching to speed up recently used applications, menus, etc. This is how memory should be used.

---

### Post by aysiu on 2006-12-01
Read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by fiery on 2006-12-01
You can also add parts of the system monitors to your gnome panel by:

Right click the gnome panel,
Choose 'Add to panel',
Go down to the 'System and Hardware' section,
Choose the 'System Monitor' and then 'Add' it to your panel.

If you want to show more than just your CPU usage:
Right click the display on the panel,
Choose 'Preferences',
Under the Monitored Resources section, just tick whichever box/resource you want to monitor.

Fairly painless! :)

---

### Post by johnmxg12 on 2006-12-01
hey thanks a lot guys, you've all been very helpful.

---

### Post by Furiattl on 2008-03-25
Yeah thanx that was cool.
I have seen some quasi transparent system monitors displayed on the desktop.
How do you get one of them to work? How do you find them, how do you install them?
Thanks

---

### Post by Shazaam on 2008-03-25
If you want to get into the nuts and bolts of memory usage type this in terminal........
```
top
```
To get  more usage info install htop. It works using the terminal too. Once you have htop running be sure to scroll down in the terminal window to see more.

---

### Post by Furiattl on 2008-03-25
Nice one.
I was thinking of something more like some eye candy, a plug in on a desktop.

---

