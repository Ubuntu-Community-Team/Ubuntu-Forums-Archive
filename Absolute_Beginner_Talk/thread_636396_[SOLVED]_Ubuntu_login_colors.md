---
title: "[SOLVED] Ubuntu login colors"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-12-09
Okay, I've been customizing my system quite a bit over the last week with little design tweaks and such, but one thing that's still bugging me is the Ubuntu color that shows up after you log in.

To clarify, I log in (login screen is custom) and then hit enter.  Then pops up the loading splash screen, but the color that fills the whole screen behind it is still the default flesh tone ubuntu has.  Then it loads the desktop.  Is there anyway to change this middle-man color?

---

### Post by jordanmthomas on 2007-12-09
system --> administration --> login window
In the themes tab (I believe) is an option for background color.
Change it.

---

### Post by philinux on 2007-12-09
yes.

system >admin > Login window

click local

look at the background colour

---

### Post by prodigalson666 on 2007-12-09
Alternatively:

Code:

gksu gedit  /etc/gdm/PreSession/Default

Change line 61 from #dab082 (peach) to #<anycolorcode>

---

### Post by Lvcoyote on 2007-12-09
Wow, I learn more each day... Thanks for the info.  While looking around in that log on window area I also found how to change that annoying bongo drum roll that plays when you reach the log in screen...... glad thats gone.... LOL

---

### Post by CryptiniteDemon on 2007-12-11
> **prodigalson666 said:**
> Alternatively:

Code:

gksu gedit  /etc/gdm/PreSession/Default

Change line 61 from #dab082 (peach) to #<anycolorcode>

Thanks, that worked.  But the graphical option didn't work for all the other suggestions.  I already knew about that option and it never did anything.

This is why I like editing from the terminal and text files more.  It always seems to work easier than the GUI.

But thank you sir.

---

