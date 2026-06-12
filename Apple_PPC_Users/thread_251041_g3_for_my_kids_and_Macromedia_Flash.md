---
title: "g3 for my kids and Macromedia Flash"
date: 2006-09-04
forum: Apple PPC Users
---

### Post by turbotuba on 2006-09-04
I was given an iMac g3. I want it to be for my kids, but they mainly use the computer for some educational websites that require flash. I've read that flash on older ppc's are not supported. Is this true? If so what can I do? I've tried to install wine but with no luck. My thinking was to get wine and install ie with flash. Would that even work anyway? Anyone have any suggestions? 
XUbuntu-6.06.1 

$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

$ sudo gedit /etc/apt/sources.list
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5384): WARNING **: Could not load python module modelines


** (gedit:5384): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5384): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5384): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5384): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5384): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
/bin/sh: /usr/bin/esd: No such file or directory

** (gedit:5384): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

####This is what i put in the source.list#####
## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by footos on 2006-09-05
mate, sorry to be the bearer of bad news but wine won't work on powerpc linux just as windows its self won't on a powerpc either. mainly it just comes down to the fact that windows runs on x86 processors so yeh ... my guess would be to try the new version of flash...sorry to dash your hopes there but yeh cya

---

### Post by 3rdalbum on 2006-09-05
Unfortunately, Flash on PowerPCs is non-existant. If you're really eager you could go and download a CVS version of Gnash, but it doesn't play many movies yet.

---

### Post by bunny64 on 2006-09-05
o_O; Orr... you could run Mac OS 9.2 -> X. I ran Macromedia Flash perfectly well from 9.2 to 10.4 on a G3 700 and have seen it running perfectly well (allbeit a little laggy) under 10.3 on a iBook 500 and on a iMac G3 600.

I know this is a Linux forum, but Linux isn't allways the best possible solution, especially when it comes to running multimedia on older machines (and this is even more relevant when it comes to children).

A statement like:
> Flash on PowerPCs is non-existant
is compeltly unfounded and short sighted.

</RANT>

Sorry 3rdalbum, nothing personal, but the answer isn't allways: "It doesn't work on Linux so it doesn't work" *Shrugs*.

turbotuba: Consider picking up a copy of 10.2 (for performance reasons), off eBay or a retro distributor and let your children learn ^o^~!

---

