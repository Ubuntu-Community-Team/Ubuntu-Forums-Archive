---
title: "Bonobo problem"
date: 2006-06-27
forum: Apple PPC Users
---

### Post by locoblade on 2006-06-27
Finally got Ubuntu somewhat going after little luck with kubuntu. Anyway, I login the panel loads up and when it gets to the nautilus icon this error comes up:
There was a problem registering the panel with the bonobo activation server. The error code is 3. The panel will now exit."
After this I'm just left with a mouse pointer on a blank screen. I'm pretty new to linux so don't really know where to start. What does error code 3 tell me?

Mark

---

### Post by locoblade on 2006-06-27
Same thing happens in failsafe.

---

### Post by desmond_314 on 2006-07-06
same problem here and I just spent like 3 hours intalling this to have it fail on the gui launch... 

anyone? I really wanna get this going

machine is pismo 500 192 ram 10gb.. ubuntu is only OS on the disk

---

### Post by travisbickle on 2006-07-07
Had/Have the same problem on my lombard. Don't have any problems installing Xubuntu. You might wanna use that anyway on your pismo because its faster. I got Ubuntu to work by first installing Xubuntu than installing ubuntu-desktop from the package manager. But once i closed the lid on the laptop in ubuntu i got that same error again. But that is a possible workaround if you can figure out how to get it to sleep in ubuntu. It sleeps fine in xubuntu.

---

### Post by webecho on 2006-07-15
Im having exactly the same problem ... did anyone find out an answer?

This is my first ever foray into the world of linux, trying to resurrect an old G3 powerbook and put it to some use

---

### Post by consultlinks on 2006-07-21
Hello, 
I am having the same problems, I have successfully installed dapper on 6 out of 10 MAcG4 laptops.  Using the same media.  You can log on to the system using a failsafe terminal window.  Extensive searches have not led me to far. 
Any information you can provide on the subject would be appreciated.

Thanks

---

### Post by consultlinks on 2006-07-21
Here is some progress on this issue. 

When booting up into xsession under options as soon as you bootup. ( use safe x terminal)  run the following commands. 
1.) startx
2.) gnome-wm 
this for some reason reset the display windows and when you type 
3.) exit it will restart gnome.  
4.) Select log in anyway.
when prompted to delete any of the applets select no. 

This got me to gnome desktop at which I can make modification using the GUI.

Hope this helps!!!!

---

### Post by thawn on 2006-08-05
It may be a problem with the clock setting. try to log onto the console (strg+alt+f1) with your username and set the date correctly before logging on:
```
sudo date --set "2006/07/07"
```
for me it also helped to be connected to the internet since then the clock was set automatically.

see also [this thread]("http://www.ubuntuforums.org/showthread.php?t=20295")

---

