---
title: "Mouse middle button"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by mystically on 2007-04-07
I use ubuntu on a laptop, in vmware. the mouse works fine but except in firefox where I can middle click so a tab appears middle click don't work elsewhere. Forexample, if in firefox or viewing files where there are too many files to fit into the screen I should be able to scroll down using the middle scroll on mouse but that doesn't happen. I can live without it but It be good to have.

---

### Post by userundefine on 2007-04-07
Check your /etc/X11/xorg.conf file.  You should have a line under "Configured Mouse" that reads Option "ZAxisMapping" "4 5".   If you do not, here's how you can add it using the terminal:

```

we'll first make a backup of the working configuration if you make a mistake
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
now open the file
**gksudo gedit /etc/X11/xorg.conf**
scroll to the part that says:
[b]Section "InputDevice"
Identifier "Configured Mouse"[/b]
check to see that this setting, 
**Option "Protocol" "ImPS/2"**
exists, and if it doesn't correct the Protocol to look like this.  Then add
**Option "ZAxisMapping" "4 5"**
before this part, which closes the mouse settings:
**EndSection**
Save the file.

```

Now hit Ctrl+Alt+Backspace to restart the X server which reloads the configuration file.  You shouldn't be dropped back to command line if you did exactly these steps, but in case you are to get your GUI running again type **sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf**, which will reinstate your backup.

---

### Post by DonoFL on 2007-04-08
Hello,

I am having a similar problem.   When I depress the middle mouse button in any file or program, such as Firefox, the mouse icon does not change to an arrow pointing up or down .... which if you did get the icon you could then just move the mouse up or down and it scrolls up or down?  Does that make sense?

I can scroll with the middle mouse button by just rolling it up or down.. but this takes forever compared to depressing it and getting the up or down icon that I mentioned above!

I made the changes to the xorg.conf file but it didn't work.

Any suggestions would be helpful.

Thx in advance!


Donovan

*EDIT*

ok.. I found out how to make it work with in Firefox anyway.

Click on **EDIT** then **Preferences** click on the **Advanced Tab** at the top, then in the center of the section find **Browsing**, click on the first choice, **Use autoscrolling.**

Hope this helps everyone!

:)

---

### Post by userundefine on 2007-04-08
> **DonoFL said:**
> I can scroll with the middle mouse button by just rolling it up or down..

I made the changes to the xorg.conf file but it didn't work.
Those changes are specific to scrolling up and down with the wheel, not autoscroll.  Glad you got it to work though.

---

