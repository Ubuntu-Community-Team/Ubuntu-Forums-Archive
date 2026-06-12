---
title: "Lost panels in XFce desktop"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by YoYoSan on 2007-11-16
For some reason I've lost both top and bottom panels on my desktop.

Tried using xfce settings manager, but no response from the panel button.

Any pointers gratefully received!

running Xubuntu 7.04 & xfce desktop.

Cheers

---

### Post by vambo on 2007-11-16
See if this is any help
[http://ubuntuforums.org/showthread.php?t=608389]("http://ubuntuforums.org/showthread.php?t=608389")

---

### Post by YoYoSan on 2007-11-16
Yeaay - good stuff cheers.

Seems like a common problem - is it related to a known bug?

---

### Post by vambo on 2007-11-16
There's one somewhere I'm sure (launchpad that is), but don't have it to hand.

---

### Post by YoYoSan on 2007-11-16
Thanks Vambo.

---

### Post by Inxsible on 2007-11-16
You can also do this. I use gnome, so I will use gnome terminologies. Please change accordingly to your xfce equivalents

In System>>Preferences>>Sessions. Go to the second tab (forgot the name - and I am @work on XP :( ) where it lists all the processes.

In there look for gnome-panel (xfce4-panel - for you guys I suppose). You would probably see the style and state for each. Change the State to 'Restart'. This means that in case the panels crash, they will restart immediately.

Then save and then open a terminal and do a ```
killall gnome-panel
``` It will kill the current panels, and because you made them "restartable" they should come back up immediately. You may or may not have to reboot in between, I forget. :confused:

This way you won't have to keep a terminal window open and neither have to worry about starting it in the background. It will automatically start, if it crashes.

---

### Post by vambo on 2007-11-16
> **Inxsible said:**
> You can also do this. I use gnome, so I will use gnome terminologies. Please change accordingly to your xfce equivalents

In** System>>Preferences>>Sessions**. Go to the second tab (forgot the name - and I am @work on XP :( ) where it lists all the processes.

In there look for gnome-panel (xfce4-panel - for you guys I suppose). You would probably see the style and state for each. Change the State to 'Restart'. This means that in case the panels crash, they will restart immediately.

Then save and then open a terminal and do a ```
killall gnome-panel
``` It will kill the current panels, and because you made them "restartable" they should come back up immediately. You may or may not have to reboot in between, I forget. :confused:

This way you won't have to keep a terminal window open and neither have to worry about starting it in the background. It will automatically start, if it crashes.

No such option under xfce, nor is there anyway (that I'm aware of) to set a "restart" flag

---

### Post by Inxsible on 2007-11-16
> **vambo said:**
> No such option under xfce, nor is there anyway (that I'm aware of) to set a "restart" flag
Aah !!

Futile effort then on my part. Sorry :(

So can you post a screenshot of your System>>Preferences>>Sessions  and the second tab? Maybe the nomenclature is different

---

### Post by YoYoSan on 2007-11-16
Sorted now thanks using the thread vambo posted.

---

