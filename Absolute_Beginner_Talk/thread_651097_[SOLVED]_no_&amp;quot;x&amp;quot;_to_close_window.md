---
title: "[SOLVED] no &amp;quot;x&amp;quot; to close window?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by alabandit on 2007-12-27
i have no x to close a window in my gusty, or maximize or minimize. this happens with everything in cluding basic programs and games that come with gusty by default?

---

### Post by jkblacker on 2007-12-27
Have you changed the theme at all, or is this just a blank default install?

---

### Post by alabandit on 2007-12-27
i only tried changing the theame in the hope it would start working. i'm using the ubantu studio theam now and its still not working?

thanks for your help

---

### Post by jken146 on 2007-12-27
Try ```
metacity --replace
``` and see what happens.  Do you have title bars at all?

---

### Post by Znort_Ubern00b on 2007-12-27
do you have an nvidia card?
is compiz running?

if yes to both type this in terminal.

**sudo nvidia-xconfig --add-argb-glx-visuals -d 24**

should allow you to see  the title bar of window.

---

### Post by alabandit on 2007-12-27
that works! BUT when i restarted to make sure it stayed it all disapeared again

[IMG]http://i61.photobucket.com/albums/h80/alabandit/no_x.jpg[/IMG]

no i don't think i have title bars but heres a screen shot

---

### Post by jken146 on 2007-12-27
OK, then your problem is that metacity (the window decorator) is not running when it should be.  Next thing is to figure out how to make it run when you log in.

From the metacity man page: > --replace
              a window manager which is running is replaced  by  metacity.
              Users  are  encouraged to change the GNOME window manager by
              running the new WM with the --replace  or  -replace  option,
              and subsequently saving the session.


So you need to tart metacity as I described in my previous post, then save your session (System > Preferences > Sessions, I think).  Then log out and in again (or better still restart X with Ctrl+Alt+Backspace) and tell us if that did the trick.

---

### Post by rich.bradshaw on 2007-12-27
It's a problem with Compiz - as mentioned earlier, some nvidia cards have a problem.

If it doesn't bother you not running Compiz for now, go to system/pref/appearance, then desktop effects and choose off. That will use metacity instead of compiz.

---

### Post by JillSwift on 2007-12-27
Are you using "Desktop Effects", and if so, did you install the advanced settings manager?

You might have the Compiz-Fusion plug-in "Window Decoration" turned off.

---

### Post by alabandit on 2007-12-27
after posting i saw znort post tried it and restarted, and it worked 

thanks for you help!

---

### Post by Znort_Ubern00b on 2007-12-27
you already did it...

no worries.

ps dont forget to mark solved.

---

### Post by cchevy on 2007-12-29
I disabled RESIZE INFO in compiz settings and it got the buttons back.

---

