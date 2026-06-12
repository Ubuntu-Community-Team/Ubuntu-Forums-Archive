---
title: "Gedit gives error message"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by dfor50 on 2006-07-10
This is the message I get from gedit

ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5264): WARNING **: Could not load python module modelines


** (gedit:5264): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5264): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

There is more lines of the same thing. I have gone to the synaptic package manager but I don't have a package for gtksourcview listed.

How can I repair gedit? Indeed is there a "repair system files" like in windows xp option?

---

### Post by Maggot on 2006-07-10
Did you try to reinstall gedit?  Sounds like some files are missing.

Do you get this error when initially opening gedit or are you opening a file?

---

### Post by GregC on 2006-07-11
I have the same problem.  I tried reinstalling gedit, python, and python2.4-gnome2-desktop, all to no avail. ](*,) It looks like the the gedit code cannot find the externally defined value for gtk_source_view_set_highlight_current_line (I'm a missing a library?).  The bad or missing constant is documented out at the gtksourceview project site at : 

[http://gtksourceview.sourceforge.net/docs/GtkSourceView.html#gtk-source-view-set-highlight-current-line](http://gtksourceview.sourceforge.net/docs/GtkSourceView.html#gtk-source-view-set-highlight-current-line)

I tried rolling gedit and gedit-common back to version 2.14.2-0ubuntu from 2.14.3-0ubuntu, but that did not help.  Also tried reinstalling libgtksourceview1.0-0, still no joy.  I know there are other editors out there, but this one is handy, and used to be dependable...

The error I get is :

ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:10604): WARNING **: Could not load python module modelines


** (gedit:10604): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
sys:1: Warning: IA__g_object_set_valist: object class `GeditView' has no property named `highlight_current_line'
gedit: symbol lookup error: gedit: undefined symbol: gtk_source_view_set_highlight_current_line

Any help is much appreciated!

Thanks,

GregC

---

### Post by GregC on 2006-07-12
Found it!  gedit is working now. I had to uninstall a previous binary install of mono with

/opt/mono-1.1.13.2$ sudo ./uninstall

It appears there was a conflict with the mono-installed libgtksourceview.so which I then pointed to with $LD_LIBRARY_PATH and $PKG_CONFIG_PATH

LD_LIBRARY_PATH=/opt/mono-1.1.13.2/lib:
PKG_CONFIG_PATH=/opt/mono-1.1.13.2/lib/pkgconfig:

I think I'd made this change a while back to fix some problem with MonoDevelop. Anyway, "sudo ./uninstall" did the trick, gedit works now.  

Hope this helps!

GregC

---

### Post by Maggot on 2006-07-12
> **GregC said:**
> Found it!  gedit is working now. I had to uninstall a previous binary install of mono with

/opt/mono-1.1.13.2$ sudo ./uninstall


Well done :cool:

---

### Post by dixonstalbert on 2006-07-13
thanks for the fix!

gedit started giving errors after I restored my home directory from breezy (with mono config files) into a fresh install of Dapper a month ago but I couldnt find any solutions.

I googled the gedit error code but didnt get any hits- 

How did you find out it was a conflict with monos libgtksourceview?????

---

### Post by GregC on 2006-07-13
You're quite welcome, glad I could help!

A couple of things led me to the mono version of libgtksourceview, the first of which was this line:

gedit: symbol lookup error: gedit: **undefined symbol:** gtk_source_view_set_highlight_current_line

**undefined symbol:** errors like this are often a version problem because the program would fail to link in the compile and build process with an undefined symbol.  

A google search on gtk_source_view_set_hightlight_current_line showed it to be a valid value (not a typo) and part of the gtksourceview library (see link in previous post).  

Next I checked the dependices of gedit in Synaptic and it reported the installed version of libgtksourceview met the requirements.  This meant I must be overriding the normal system library somewhere, as that is where Synaptic gets its information normally.  

The environment variables LD_LIBRARY_PATH and PKG_CONFIG_PATH override, or more accurately "prefix" the dynamic and build library paths when defined.  So as soon as I found an older libgktsourceview.so version pointed to by these variables,  I was pretty sure I'd found the culprit.  

Having built mono from source a couple of times, I was aware of mono's, or more specifically, of MonoDevelops dependecy on this library, and that it provides some text coloring capabilities, so that made sense given the names of the program/module, "modelines.py" and gtk_**"source_view"**_set_highlight_current_line.  Kudos to the developers for picking descriptive variable names.

Hope this helps!

-GregC

---

