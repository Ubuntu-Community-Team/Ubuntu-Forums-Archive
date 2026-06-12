---
title: "[SOLVED] screensaver problem"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-08-01
my screensaver will activate, run for the correct amount of time, and then make the screen go black just like it's supposed to.  but then five minutes later, it comes back on for a few minutes before making the screen black again...  sometimes it'll do this a few times before letting the screen go dead.  i have compiz fusion installed, is that doing something to it?  how can i stop this problem?  it's quite annoying to have the screensaver come back on while i'm trying to sleep in my bed (the laptop in question is five feet from where i sleep).

---

### Post by wolfen69 on 2007-08-01
are desktop effects enabled when this happens? if so, see if the screensaver does the same thing with effects disabled.

---

### Post by Niklas Schröder on 2007-08-01
nope.  i don't use desktop effects.  i use compiz fusion.  the new version of compiz.  feisty ships with the old version.  i don't think fusion's doing anything to it.  i just threw that out there just in case.

---

### Post by Chris S. on 2007-08-02
I read this yesterday, and it just now hit me what your problem may be.  Hope this helps if you haven't already solved the problem.

Are you using the gnome screensaver, the default with Ubuntu?  I read before that the gnome screensaver will cycle every x minutes as part of the random screensaver option, whether the randomize option is selected or not.  That may be causing the problem.

Use gconf-editor (type "gconf-editor" at the terminal if you don't know), go to apps->gnome-screensaver, and set the "cycle_delay" to something big, like 1000 or 10000.  I think that's the right setting.  If that doesn't work, look around there for another setting that might do the trick.

Oh, and if you aren't using gnome-screensaver, this probably won't work, but what's there to lose, right?

---

### Post by Niklas Schröder on 2007-08-02
just changed it.  i'll let you know if it works in a bit.  :)

---

### Post by Niklas Schröder on 2007-08-03
from what i saw last night, the above suggestion worked!  yay!  

kudos to Chris S.

---

