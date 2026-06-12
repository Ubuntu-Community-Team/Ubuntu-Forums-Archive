---
title: "workspace1 is slow"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-11-11
I can switch between desktop no jproblem, but when I go back to desktop 1 it takes about 20 seconds for it to switch to desktop 1.  When i switch to other desktops it switches instantly,  any ideas?????   I'm running 7.10 thanks

---

### Post by Nano Geek on 2007-11-12
Do you have any programs open on that workspace?

---

### Post by endlessurf on 2007-11-12
just fire fox, but I allso have programs running on the other desktop and it switches between them no problem

---

### Post by Nano Geek on 2007-11-12
That's weird. Are you running Compiz?

---

### Post by endlessurf on 2007-11-12
yeah, I think it is a compiz problem,  when i use my right click to make more desktops i can switch between any of them easily.  then i use my right click to set the number of desktops to 1.  I then go into compiz and set it at 4 and that is where my problem is.  The reason why i am using compiz is because I can only get wmctrl to work with compiz.

---

### Post by Nano Geek on 2007-11-12
What kind of graphic card do you have?

---

### Post by spupy on 2007-11-12
Move firefox to another workspace and see if the workspace with firefox on is the one that opens slow?

---

### Post by endlessurf on 2007-11-12
it is slow with just terminal running
I went to synaptic and removed it completely.  restarted, then installed it again.  Still have the same problem

---

### Post by endlessurf on 2007-11-13
so i did a fresh install and I still have the problem.  After fooling around with the settings I have figured out if i set the "horizontal Virtual Size" to four, i can rotate to any desktop no problem.  When I adjust "horizontal Virtual Size" to 0 and adjust "Number of Desktops" to four, this is where the problem occurs.  any ideas.... thanks

---

### Post by Nano Geek on 2007-11-13
> **endlessurf said:**
> so i did a fresh install and I still have the problem.  After fooling around with the settings I have figured out if i set the "horizontal Virtual Size" to four, i can rotate to any desktop no problem.  When I adjust "horizontal Virtual Size" to 0 and adjust "Number of Desktops" to four, this is where the problem occurs.  any ideas.... thanksI'm glad you got it working. It could be that it was trying to draw two desktops at the same time or something when "horizontal Virtual Size" was set to 1. Anyway, I'm glad it's working again.

---

### Post by mcduck on 2007-11-13
> **endlessurf said:**
> so i did a fresh install and I still have the problem.  After fooling around with the settings I have figured out if i set the "horizontal Virtual Size" to four, i can rotate to any desktop no problem.  When I adjust "horizontal Virtual Size" to 0 and adjust "Number of Desktops" to four, this is where the problem occurs.  any ideas.... thanks

Well, the normal configuration _is_ to have as high number in Horizontal Virtual Size as you need separate desktops, and keep the other settings at one. I would recommend just keeping it that way, if it works without any problems..

Horizontal Virtual Size tells how many sides you want to have on your 'cube', and Number of Desktops tells how many separate cubes you want to have.. So if you have horizontal size of 4 and number of desktops 4 you actually get 4 cubes, each with 4 sides..

---

### Post by endlessurf on 2007-11-13
thanks for the reply, my issue is, I am running a touch screen and I need to run a command to rotate to a new screen.  After wondering around I stumbled in to wmctrl to rotate to a new desktop.  The problem is wmctrl does not work with virtual desktops.  I did not have this problem when i was running 64 fawn.  I was wondering if any of you know how to rotate a virtual desktop?????? Thanks

---

### Post by mcduck on 2007-11-13
> **endlessurf said:**
> thanks for the reply, my issue is, I am running a touch screen and I need to run a command to rotate to a new screen.  After wondering around I stumbled in to wmctrl to rotate to a new desktop.  The problem is wmctrl does not work with virtual desktops.  I did not have this problem when i was running 64 fawn.  I was wondering if any of you know how to rotate a virtual desktop?????? Thanks

If you have Compizconfig Settings Manager installed, you can use it to define keyboard shortcuts for moving to next/previous desktop, or to move directly to a certain desktop.

If youa re using the Cube plugin, make sure 'Rotate Cube' is also enabled. Then the settings for shortcuts are in Rotate Cube/Actions/General.

If you _only_ have a touch screen, and no keyboard, you can also configure it to rotate to another desktop by touching screen edges.

---

### Post by endlessurf on 2007-11-13
touching the edges won't work to well.  I would have to redo my myth theme.  I will set up 5 desktops and only use 4.  The user interface is only set up for 4 workspaces.  I was wondering is there a way to let say execute ctrl+alt+7 from a script....?????

---

