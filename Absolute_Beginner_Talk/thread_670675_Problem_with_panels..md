---
title: "Problem with panels."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-17
Here goes...

I have 2 panels, the standard one at the bottom that comes right after install with the workstations and open items list and show desktop button, and I took the top one that comes standard with installation and turned it into a smaller one that doesn't expand.  The top one is smaller and has the "hide buttons" so that I can shoot it to either side if I choose.  Every time I boot up it's just sitting in the middle of the screen and almost looks frozen.  I have to right-click on one of the hide buttons and go to properties and expand it to go to the top then un-check expand for it to shrink back down to normal and stop looking frozen.

What could be the cause of this and also how can I get it to just start at the top like i want it?

---

### Post by Hospadar on 2008-01-17
sounds like a bug in the panel software, you could try deleting the panel and re-creating it, there might be something in it's configuration file doing that.

---

### Post by ladybumavere on 2008-01-21
> **Hospadar said:**
> sounds like a bug in the panel software, you could try deleting the panel and re-creating it, there might be something in it's configuration file doing that.

I've tried to re-make it but it's the main panel, aka the one that has applications, places, system and all that jazz on it.  I attempted re-making it and I was extremely unsuccessful.  Any other ideas?

---

### Post by spiderbatdad on 2008-01-21
heres a screen shot of my panels...as you can see, they are completely remade. just the result of fooling around...making sure objects are locked. remembering the current session under preferences>>sessions>>session options. I don't think I changed anything in gconf-editor>>apps>>panel>>global. of course if you click the screenshot again after it's opened, it enlarges for clairity.

---

### Post by mgmiller on 2008-01-21
> I have 2 panels, the standard one at the bottom that comes right after install with the workstations and open items list and show desktop button, and I took the top one that comes standard with installation and turned it into a smaller one that doesn't expand. The top one is smaller and has the "hide buttons" so that I can shoot it to either side if I choose. Every time I boot up it's just sitting in the middle of the screen and almost looks frozen. I have to right-click on one of the hide buttons and go to properties and expand it to go to the top then un-check expand for it to shrink back down to normal and stop looking frozen.

My system did the exact same thing, with the same "fix" you use to get the panel back at the top.  It started after I played around with multiple monitors and then went back to just 1.

I never did figure out how to fix it, I just kept putting the panel back on the top and one day it just stayed there and hasn't given me a problem since.

Adding the Applications, Places System thing back in is easy, its called Menu Bar in the add to panel dialog.  The others are Notification Area, Clock and Quit.

To add the buttons for Firefox and Evolution, click on Applications, Internet and then right click Firefox web browser and select "Add to Panel".  Finally do the same for Applications, Office > Evolution.

Once they are in place on the panel, you can right click an icon and then click move and slide your mouse to where you want it then left click to put it there.  When every thing is where you want it, right click each item and click "Lock to Panel".  Then right click the panel and in properties deselect expand and click to add the hide buttons and you should be back where you started.

---

### Post by ladybumavere on 2008-01-22
> **mgmiller said:**
> My system did the exact same thing, with the same "fix" you use to get the panel back at the top.  It started after I played around with multiple monitors and then went back to just 1.

I never did figure out how to fix it, I just kept putting the panel back on the top and one day it just stayed there and hasn't given me a problem since.

Adding the Applications, Places System thing back in is easy, its called Menu Bar in the add to panel dialog.  The others are Notification Area, Clock and Quit.

To add the buttons for Firefox and Evolution, click on Applications, Internet and then right click Firefox web browser and select "Add to Panel".  Finally do the same for Applications, Office > Evolution.

Once they are in place on the panel, you can right click an icon and then click move and slide your mouse to where you want it then left click to put it there.  When every thing is where you want it, right click each item and click "Lock to Panel".  Then right click the panel and in properties deselect expand and click to add the hide buttons and you should be back where you started.



Hmm, well I guess until someone can find out what causes this I'll just have to continue to use the makeshift fix.

At least I know someone else is having the same problem, so it's not just me.

:)

---

