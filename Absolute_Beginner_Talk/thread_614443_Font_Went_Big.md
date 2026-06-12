---
title: "Font Went Big"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-15
For some reason the font on all my title bars just got really big without me noticing.  What happened? how do i change this back?

Examples:
my firefox browser title bar is large font
the title bar of my terminal is large font

how did i change this? how do i change it back?

---

### Post by ramjet_1953 on 2007-11-15
Navigate to:

[COLOR="Blue"]System>Preferences>Appearance[/COLOR]

When the window opens, click on the [COLOR="Blue"]Fonts Tab.[/COLOR]

Now alter the settings to suit yourself.

Regards,
Roger :cool:

---

### Post by jordank on 2007-11-16
my font for my titlebar doesn't seem size 10 as the fonts menu declares. i didnt ever go to the fonts menu before that either. 
here's a screenshot.
other suggestions?

---

### Post by jordank on 2007-11-16
and i also checked to see if the bold setting was the problem - it's not.  Font is still quite large.

---

### Post by jordanmthomas on 2007-11-16
If I remember correctly, you're using emerald as your window manager, no?
If so, the settings for its fonts are done in emerald-theme-manager and it doesn't respect the ones from gnome-appearance-properties.

---

### Post by jordank on 2007-11-16
These seem like normal settings, i definitely never went in and changed them.  notice the large font

---

### Post by jordanmthomas on 2007-11-16
If it's ONLY your titlebar fonts that seem too large, there's nothing to do but change it in emerald-theme-manager.

If it's all your fonts that seem too large, try changing your dpi in gnome-appearance-properties in the font section.

It is odd, though.  My Sans 10 is the exact same as yours, but my bold Sans 9 is much smaller.  (I have compiled a special font renderer, which is probably why, but it's odd that 10 matches yours and 9 doesn't)

---

### Post by jordank on 2007-11-16
haha emerald has given nothing but probs/

---

### Post by jordanmthomas on 2007-11-16
Switch back to gtk-window-decorator?

---

### Post by Xivanari on 2007-11-16
I definately am having the exact same problem, however I do NOT use the emerald theme manager.  I just installed ubuntu 2 days ago and havent even had time to mess around with it much, rebooted it a few times and now all my titlebar fonts and login screen fonts are all out of whack.  Help please?

---

### Post by LanDroid on 2007-11-16
> **jordanmthomas said:**
> If it's ONLY your titlebar fonts that seem too large, there's nothing to do but change it in emerald-theme-manager.

If it's all your fonts that seem too large, try changing your dpi in gnome-appearance-properties in the font section.  ...
> Switch back to gtk-window-decorator?

I have the same problem, but remember we're in the "absolute newb" section, so how does one figure out if emerald theme mgr is being used and how do we get out of it?  In System>preferences>Appearance>Theme it lists "Crux". 

I reduced font size in System>Preferences>Appearance and no change.  Increased dpi slightly, no change.  What does "Switch back to gtk-window-decorator?" mean?

---

### Post by Xivanari on 2007-11-16
yea cmon make it nice for us newbs! :D

---

### Post by jordanmthomas on 2007-11-16
Sorry about that.  :)  I just assumed that if you managed to load emerald instead of the normal window decorator that you'd know how to change it back too.

One way to see if you're using emerald is to run emerald-theme-manager and select another theme from the list.  If your windows change, you are using emerald.  If they don't, you're not.

Another way (and the way I would do it myself) would be to run
```
ps -A | grep emerald
``` in a terminal.  This lists all the processes you have running and then gives the list to grep which searches for "emerald".  If nothing is output, emerald is not running.

Now, I am going to frank with you.  I am not sure what methods Ubuntu has for swithing between the decorators.  In arch, I run fusion-icon and get something that looks like this:
[img]http://img267.imageshack.us/img267/2003/snapshot9qa7.png[/img]

A surefire way to make sure you're running gtk-window-decorator is this:
```
killall emerald
killall gtk-window-decorator
gtk-window-decorator --replace
```
At least one of these lines will give you an error.  If it's one of the first two don't worry about it.  The last one should not fail.

> What does "Switch back to gtk-window-decorator?" mean?
I'll try to explain this as best I can.  Compiz is a window manager, and it has several window decorators.  The two you probably have installed are gtk-window-decorator and emerald (actually you probably don't have emerald installed, but the OP did).

The main difference in these is that gtk-window-decorator uses the theme specified in your appearance properties (which are actually metacity themes) and emerald uses its own themes that you change with emerald-theme-manager.  As for how to switch between them, see above.


Finally, to talk about the fonts again after that tangent:  does changing the font to another font entirely change it or does it still look the same no matter what font you choose?

---

### Post by jordank on 2007-11-16
A simple reboot did the trick, btw. :)

---

### Post by jordanmthomas on 2007-11-16
:lolflag:

---

### Post by LanDroid on 2007-11-16
I think what worked for me was reducing the font size from 10 to 6 in System>Preferences>Appearance and then rebooting.  After reboot the title bars looked really tiny.  I switched the font size back to 10 and Bob's your uncle, it looks great.  So far so good, hope that doesn't keep happening.  So we kinda stumbled on something that works...  \\:D/

On edit:
Oooops, after another reboot, I'm back to big fonts.  Oh well...

Another update:
Disabling all visual effects in System>Preferences>Appearance appears to have fixed it.

---

