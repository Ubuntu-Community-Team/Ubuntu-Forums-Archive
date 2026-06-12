---
title: "Openshot won't start"
date: 2013-08-06
forum: Any Other OS
---

### Post by matt9 on 2013-08-06
hi guys

Running Openshot on elementary beta 2, and cannot get it to start.  From GUI, just nothing happens, from the command line, I followed the suggestions as far as my lil-noob-self felt confident.

See below:

```
matt@matt-hp:~$ openshot

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------


(process:14652): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
--------------------------------
   OpenShot (version 1.4.0)
--------------------------------
Process no longer exists: 14548.  Creating new pid lock file.


------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: unsupported locale setting
----------------------------------------------------------------


OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:


Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.


       $ python
       >> import mlt
       >> mlt.Factory().init()


Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at https://bugs.launchpad.net/openshot.  Good luck!


matt@matt-hp:~$ python
Python 2.7.3 (default, Apr 10 2013, 06:20:15) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import mlt
>>> mlt.Factory().init()
No LADSPA plugins were found!


Check your LADSPA_PATH environment variable.
<mlt.Repository; proxy of <Swig Object of type 'Mlt::Repository *' at 0x7fbdf4ec6d20> >



```

Any ideas/suggestions?

Thanks

Matt

---

### Post by Cheesemill on 2013-08-06
*Thread moved to **Other OS/Distro Support**.*

---

