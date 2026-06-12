---
title: "Quick question from a newb (configuring)"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by RoboBradley on 2008-03-09
I screwed up my graphics display from the System->Administration->Graphics and Display menu, to the point where I couldn't make out anything on the screen to fix it. Someone suggested a few things to run from recovery mode, but they didn't work. Long story short, I re-installed Ubuntu (for other reasons). 

I now realize that if I had configured the file from the command line, I could have backed it up beforehand. However, it wasn't clear which file was being reconfigured from the GUI window. My question is: how can I tell -- in general -- which file is being edited/reconfigured through a GUI window so that I can back it up before proceeding any further (or perhaps even close the window and switch to command line reconfiguring)?

---

### Post by 1010011010 on 2008-03-09
In general - /etc/X11/xorg.conf

---

### Post by RoboBradley on 2008-03-09
> **1010011010 said:**
> In general - /etc/X11/xorg.conf

Thanks for the quick reply. Is that for graphics only? I'm wondering about anything that can be reconfigured from the drop-down menu. How can I tell which file is actually being edited, for any application?

Thanks.

---

### Post by szymon_g on 2008-03-09
hm... you can modify 

/etc/X11/xorg.conf 

manually or run

sudo dpkg-reconfigure xserver-xorg from terminal (alt + ctr + f(n)) - works only when xorg is off (sudo killall -9 Xorg & gdm)


/////////////////
eh, to late :/

---

### Post by RoboBradley on 2008-03-09
The command:

sudo dpkg-reconfigure xserver-xorg -phigh

is exactly the one that wasn't working :( Anyway, everything is re-installed, and I now see that all the input devices and such are listed in that file. Thanks!

---

