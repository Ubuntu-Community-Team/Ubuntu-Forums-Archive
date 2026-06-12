---
title: "gDesklets help"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2007-11-23
I've been using gDesklets for a while...now i've installed AWN and for some reason the desklets are no longer appearing: when i launch the application the gDesklets Shell come up for a second and then disappear without launching my desklets :confused::confused:

---

### Post by taurus on 2007-11-23
Try running it from a terminal to see what's wrong with it.

```
gdesklets
```

---

### Post by nikolas68 on 2007-11-23
...still nothing, this i s what i get:

```
Starting gdesklets-daemon...
Connected to daemon in 520 milliseconds.
```

but still not starting...

---

### Post by nikolas68 on 2007-11-28
....still haven't been able to have it running. I've re-installed but still nothing. This is what i get if i open the Log Messages:
```

Log messages of /home/nicola/.gdesklets/logs/gdesklets%3A0.0.log                     
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is  
deprecated, use gtk.gdk.threads_init instead                                         
  gtk.threads_init()                                                                 
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module tiling: This Python has API version 1013, module tiling has      
version 1012.                                                                        
  module = _old_imp(name, globs, locls, fromlist)                                    
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module x11: This Python has API version 1013, module x11 has version    
1012.                                                                                
  module = _old_imp(name, globs, locls, fromlist)                                    
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module systray: This Python has API version 1013, module systray has    
version 1012.                                                                        
  module = _old_imp(name, globs, locls, fromlist)                                    
/usr/lib/gdesklets/gdesklets-daemon:119: GtkDeprecationWarning: gtk.threads_enter is 
deprecated, use gtk.gdk.threads_enter instead                                        
  gtk.threads_enter() 
```

---

