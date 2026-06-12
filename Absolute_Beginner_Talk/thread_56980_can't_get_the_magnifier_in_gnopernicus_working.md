---
title: "can't get the magnifier in gnopernicus working"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by yellowband on 2005-08-14
Hey guys,
thanks for all of the help so far. ihave ubuntu working successfully with my ATI graphics acceleration working properly woo.

I'm still having trouble getting the magnifier in gnopernicus working.  I installed gnopernicus and all dependencies from synaptic and everything seemed to go ok.  When i run gnopernicus my computer speaker (not normal speakers) makes a beep. The program loads but nothing happens. I can access all of the programs menus and whatnot but no screen magnification.  I'm not even sure where to start to diagnose this problem.  I run it from applications>accessability>screen magnifier.  

any help would be much appreciated.  Thank you

---

### Post by yellowband on 2005-08-15
no ideas?

what if i ran it from a terminal?  what command do i type to run it from there?

---

### Post by yellowband on 2005-08-16
I treid running gnopernicus in the terminal and this is the error message i got. maybe somebody can help me from it

Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
GTK Accessibility Module initialized

(gnopernicus:9259): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Bonobo accessibility support initialized

(gnopernicus:9259): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible

**********************
* SCREEN READER CORE *
**********************


(srcore:9260): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Bonobo accessibility support initialized
GTK Accessibility Module initialized

(srcore:9260): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible

** ERROR **: Could not locate registry
aborting...

(gnopernicus:9259): gnopernicus-WARNING **: srcore exited.

---

### Post by Henrik on 2005-08-18
I think you need to install 'gnome-mag' separately from synaptic. The reason it is not a strict dependency is that Gnopernicus runs without it and that magnification is an 'optional' feature. I agree that this is not optimal and should certainly be documented better. You might need to reboot as well.

It works for me now. (can't get speech to work yet though, any luck on this?) 

If you do any testing of these features, please report any findings [here](https://wiki.ubuntu.com/BreezyAccessibilityStatus). Thanks :)

---

