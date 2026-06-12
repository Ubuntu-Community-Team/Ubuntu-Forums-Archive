---
title: "&quot;Funny&quot; problem with XaoS"
date: 2008-01-01
forum: Art &amp; Design
---

### Post by Don1500 on 2008-01-01
I enjoy fractals and like the designs. I had just installed Gusty and didn't have my ATI card installed right but XaoS worked great, got some really good designs. I installed the restricted drivers and got the ATI crad running right, opened XaoS and it was transparent! I can save the screen but during operation I have to adjust everything by guess because the white on white menus can't be read. 

Has anyone seen this type of thing before, with any program? Where the active window is transparent? And only for one program?

---

### Post by got awesome? on 2008-01-02
Yeah I have the same issue, and also have an ATI card. Not really sure what to do.. but I will watch this thread.

---

### Post by Don1500 on 2008-01-05
I guess this is just too tough for you guys. 50 views and one response saying he has the same thing.

---

### Post by Anzan on 2008-01-05
I have Nvidia and it is XaoS is transparent for me as well.

---

### Post by Don1500 on 2008-01-06
OK, for a work around:
System=>Preferences=>appearance=>visual effects => NONE

Then you can use XaoS.
This bug is being worked by the XaoS working group, maybe in ver 3.3?

---

### Post by malenkylizards on 2008-02-08
Yeah, I have the same thing.  And yes, disabling all the pretty compiz settings seems to do the trick.

I'll also say that so far, I haven't been able to play any of the 3D games with compiz enabled.  It just makes it all kinds of crappy.

Only way I can do that yet is to go into System>Preferences>Appearance>Visual Effects.  What would be nice is to pop a button onto the K-bar that'll quickly enable or disable compiz...and most importantly, keep my custom settings when I return to it, that's been the biggest PITA for me yet.

I haven't yet been able to figure that out, but I'm working on it (I'm a major linux newbie, just installed Ubuntu yesterday).  Any advice?

---

### Post by red_Marvin on 2008-02-09
If you have xaos as a menu bar command you could always edit it to first turn off desktop effects like this:

Gnome menu -> settings -> main menu
find the troublesome program and click right mouse button -> properties
copy the command line into a new text document and edit it like this:
```
#! /bin/bash
metacity --replace &
sleep 2
[COLOR="Green"]*the command line you copied here*[/COLOR]
sleep 2
compiz --replace &

```
save it as something fitting like .runxaos in your home directory (notice the dot? that makes the file hidden so it won't get in your way)

Open a terminal and type *chmod +x .runxaos* -this will make the file executable

Now edit the command line in the menu item properties so that it will say */home/yourusername/.runxaos*
Good luck!

---

### Post by kovzol on 2008-03-15
Fixed in 3.3.

---

### Post by JB3 on 2008-05-01
Besides disabling desktop effects, you have several other options, in order of effort:

1) Hit Alt+F2 and run the following command: "env XLIB_SKIP_ARGB_VISUALS=1 xaos" (you could also do this in Terminal).*
2) This is fixed in XaoS 3.3; download the source from [http://xaos.sf.net](http://xaos.sf.net) and compile for yourself.
3) This is fixed in the XaoS package on Hardy; upgrade.

*You can also edit the XaoS entry in the menu to change this permanently:
1) Right click on the applications menu and choose Edit Menu.
2) Go to Applications->Graphics, 
3) Right click on XaoS and choose Properties.  The properties window may be hidden behind the main window.  If you don't see it, move the main window out of the way.
4) Change command to "env XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/xaos -driver x11" (i.e., add "env XLIB_SKIP_ARGB_VISUALS=1" in front of the original command.
5) Press the Close button on the properties window, followed by the main menu editor window.
6) Start XaoS from the Menu like normal.  It should work correctly now.

---

