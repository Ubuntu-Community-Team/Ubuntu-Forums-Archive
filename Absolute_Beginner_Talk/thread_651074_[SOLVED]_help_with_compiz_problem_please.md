---
title: "[SOLVED] help with compiz problem please"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by AndreiMe on 2007-12-27
i have an nvidia geforce fx 5500 video card with 256 ram and 128 bit color depth.
i installez beryl. it didn't work. i installed compiz-fusion, following a tutorial, it removed beryl components. i reinstalled my card using envy, just as a mater of precaution, i activated the card from restricted drivers, i installed compiz manager. i have all my desktop settings on extra. on custom it won't open preferences. i cannot add workspaces. i cannot add any effect. actually any change i make in compiz manager, they remain there active, but won't enable.
i had installed and removed 2-3 compiz managers from synaptic, this one is the only that starts.
help please!

---

### Post by jken146 on 2007-12-27
Did you install the package **compizconfig-settings-manager**?

Please post the output of the following command, run in a terminal.  ```
compiz --replace
```

---

### Post by AndreiMe on 2007-12-27
so, i have compizconfig-settings-manager installed, and when i give to command compiz --replace (alt+f2) it restarts the explorer(sorry windows addict, don't know how it's called in ubuntu, dektop environment?) and then nothing happens. It is just the same.

---

### Post by jken146 on 2007-12-27
Run the command in a terminal, not in Alt+F2 please.  If something is wrong then the terminal will display some error messages.

---

### Post by skymera on 2007-12-27
sudo apt-get install compizconfig-settings-manager

then type 

```
 ccsm 
``` in terminal

---

### Post by AndreiMe on 2007-12-28
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


this is the error that gives me when i enter ccsm in the terminal.
when i enter compiz --replace in the terminal, it restarts the desktop environment and then it dissapears.

---

### Post by AndreiMe on 2007-12-28
[IMG]http://farm3.static.flickr.com/2185/2142755685_0f3fd8f0e7_o.png[/IMG]
this is the screenshot of the installed compiz components

---

### Post by AndreiMe on 2007-12-28
sudo aptitude purge ~ncompiz ~nlibdecoration
i did this and reinstalled compiz from synaptic without trevino's rep and it works, thanks alot for your help

---

