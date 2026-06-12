---
title: "gdesklets Python problem?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by words1 on 2007-08-25
Using 7.04, Gdesklets 0.35.3.

I have Newsticker installed and it works fine when I first start it, but after a few minutes Python begins eating up my processor and freezes everything.  The log in gDesklets says:

```
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
==========================================================[08/25/07-18:09:10]===     
Adding "/home/evan/.gdesklets/Displays/NewsTicker/ticker.display" with ID            
"id11862070809563600" to the desklet list.                                           
/usr/lib/gdesklets/utils/ErrorFormatter.py:118: RuntimeWarning: Python C API version 
mismatch for module svg: This Python has API version 1013, module svg has version    
1012.                                                                                
  module = _old_imp(name, globs, locls, fromlist)                                    

```

So I guess the mismatch of Python versions could be responsible?

Anyone know of a way to fix this?

---

