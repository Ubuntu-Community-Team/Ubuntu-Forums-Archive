---
title: "gedit errors in Xubuntu."
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by A2A on 2006-08-08
HI all,
I'm running Xubuntu 6.06 on my laptop.  This morning I had to edit a config file and realized I didn't have a text editor (I only know of gedit and vi).  Since I have a preferance for gedit, I decided to add it via synaptic.  All went well and it d/loaded and installed the required libraries etc.
When I opened gedit via the terminal, I got a whole bunch of warnings and errors but the application still opened up, and I was able to use it with no problems.  
Here are the errors/warnings that I got in terminal:
> a2a@a2a-laptop:~$ gedit
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:7991): WARNING **: Could not load python module modelines


** (gedit:7991): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:7991): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
/bin/sh: /usr/bin/esd: No such file or directory

** (gedit:7991): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
a2a@a2a-laptop:~$
 
Any help or suggestions to fix this issue would be much appreciated,

Thanks

A2A

---

### Post by taurus on 2006-08-08
It's just a warning and if gedit still works, then don't worry about it!!!  Otherwise, use a text editor like nano and you don't have to worry about any warning...

---

### Post by orb9220 on 2006-08-08
or mousepad which is default gedit app in xbuntu.

---

### Post by A2A on 2006-08-08
Thank you both for prompt replies.  I'll just remove gedit from the system, because those warnings are ugly to look at :p.  Will try out nano and mousepad.

Regards,

A2A

---

### Post by orb9220 on 2006-08-08
nano runs in the term like a dos editor and mousepad is the equivalent to gedit for gui editing.

---

### Post by taurus on 2006-08-08
> **A2A said:**
> Thank you both for prompt replies.  I'll just remove gedit from the system, because those warnings are ugly to look at :p.  Will try out nano and mousepad.

Regards,

A2A
Then don't run gedit from a terminal.  Create a shortcut in the menu and start it from there...  Then, you don't have to see the warning/error message!!!

---

### Post by catphive on 2007-08-08
Could someone actually answer the question? If you don't know the answer to a question telling someone to use your favorite editor, or "just ignore the errors" is a really horrible response and is super annoying when you actually want to solve a problem.

I have a similar problem in 7.04 with gedit

/bin/sh: /usr/bin/esd: not found

warnings, and some weird sound behavior.

So how do I get gedit to work right with xubuntu's sound infrastructure?

---

### Post by zlO_Olz on 2007-08-08
> **catphive said:**
> I have a similar problem in 7.04 with gedit

/bin/sh: /usr/bin/esd: not found

warnings, and some weird sound behavior.


I''m experiencing the same issue... this error also prevents other audio programs to work properly (I tried BMPx and Rhythmbox). Does anyone have an idea on how to solve this?

thanks

---

### Post by zlO_Olz on 2007-08-08
I've just installed "esound" from Synaptic Package Manager and now gedit runs from terminal without warnings... however, I still have problems running MPBx and Rhythmbox :(

EDIT:

Solved also for Rhythbox & BMPx installing GStreamer with alsa & oss support. iupz! :)

---

### Post by domeboy on 2008-01-13
this solved my problem, thank you!

---

