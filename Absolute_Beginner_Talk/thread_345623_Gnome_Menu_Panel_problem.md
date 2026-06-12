---
title: "Gnome Menu Panel problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by agatha on 2007-01-24
Hi

Being fairly new to Linux, using Dapper, I have just managed to prevent
the drop down menu to appear under "Applications". Places and
System are OK.

Selecting 'Edit Menus' from the context menu results in the taskbar
displaying "Starting Alacarte Menu Editor" for about 15 seconds before
it extinguishes without loading.

When I select "Applications", the background colour changes, as it
should, but when I look closely I can also see a single, clear pixel
below the menu bar at the edge of the screen. There is something hiding
& I don't know how to undo it.

Anyone can tell me, I would be very happy.
BTW, reboot = no result.

Many thanks i.a.
Edit/Delete Message

---

### Post by mikewhatever on 2007-01-24
Try right clicking on the panel, and selecting Add to Panel.

---

### Post by TeeAhr1 on 2007-01-24
Hrm.  New one on me.  Just a hunch, but:

Right-click on the gnome menus and select "remove from panel"
Right-click on the panel, select "add to panel," and re-add the menu.

Like I said, just talking out my hat here, but it might do the trick.

-p.

---

### Post by ComplexNumber on 2007-01-24
can you get a screenshot? if you can't access you applications menu, right click on your desktop and select 'open terminal'. then type in 'gnome-screenshot'.

---

### Post by ardchoille42 on 2007-01-24
> **ComplexNumber said:**
> can you get a screenshot? if you can't access you applications menu, right click on your desktop and select 'open terminal'. then type in 'gnome-screenshot'.

That won't work unless he has installed nautilus-open-terminal

Another way of launching gnome-screenshot is ALT+F2, type in gnome-screenshot and click "Run". But, what he needs to do is:

1) Press ALT+F2
2) type in: gnome-screenshot --delay=5
3) during the 5 second dely, before gnome-screenshot launches, click on the gnome menus so they will appear in the screenshot.

The command "gnome-screenshot --delay=5" Will launch gnome-screenshot after a 5 second delay, allowing the user to open a menu somewhere.. otherwise, there's no way of getting menus in the screenshot.

---

### Post by xpod on 2007-01-24
Or even just hitting the printscreen button does the job

EDIT:unless you want delays i suppose.
EDIT2: aahhhh..now i see..lol

---

### Post by ComplexNumber on 2007-01-24
> That won't work unless he has installed nautilus-open-terminal
whenever i do a new install, the open-nautilus package is one of the first things that i install because its essential to me.

---

### Post by ardchoille42 on 2007-01-24
> **ComplexNumber said:**
> whenever i do a new install, the open-nautilus package is one of the first things that i install because its essential to me.

Ah, I see. Well, that is a very good app and one I should probably add to my master install script :)

---

### Post by ComplexNumber on 2007-01-24
> **ardchoille42 said:**
> Ah, I see. Well, that is a very good app and one I should probably add to my master install script :)
well, the truth is, i can't imagine it not being there. so thats probably why i assumed that agatha would have the same as me.

---

