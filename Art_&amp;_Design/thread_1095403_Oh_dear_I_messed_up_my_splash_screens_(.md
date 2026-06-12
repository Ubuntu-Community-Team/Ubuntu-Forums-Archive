---
title: "Oh dear I messed up my splash screens :("
date: 2009-03-13
forum: Art &amp; Design
---

### Post by Fenris_rising on 2009-03-13
Hi all

Rather embarrassingly I have managed to lose my default splash screens for 8.04. :-({|=  I downloaded usplash...I rather jumped in without RTFM and then I also installed splashy, please don't ask why, I must have been confused. :( .......... Yep I did I just checked my eeepc which has 8.10 easy peasy on it and that has a gui called startup manager with which I changed the splash screen with. So I am off into synaptic to see if it's available in the 8.04 repo's.

Or is there a simple solution that a numpty like me can follow :)

regards

Fenris

---

### Post by Fenris_rising on 2009-03-14
Still struggling.....Imanaged to get a startup screen back but not the exit screen. I have reinstalled splashy.........HELP?! :S

regards

Fenris

---

### Post by Orlsend on 2009-03-14
I use Epidermis theme manager,the Ubuntu default usplash its in the epidermis repo.

[http://epidermis.tuxfamily.org/](http://epidermis.tuxfamily.org/)

Its should just take 5 clicks and a few KB's to get back to normal.

---

### Post by Fenris_rising on 2009-03-14
Hi there

Thanks for the heads up. As it happened it looks like all my rooting about in the guts of the OS did some damage elsewhere. So I have re-installed the OS but am installing epidermis so, I hope, I can play around with less chance of screwing it up....Is there a catch?? :D

regards

Fenris

---

### Post by Orlsend on 2009-03-14
No catch really. we have the complete default Human theme(GDM,Usplash,Grub,Metacity,GTk....etc), Until now we haven't received an error about messing up computers. It is a standalone manager it those not use the resource data base of the default theme manager. No Harm can be done. :D

---

### Post by Fenris_rising on 2009-03-14
Hi there

Well I tried to change my usplash and although it's ticked and applied the default Ubuntu has remained. Am I missing something particular? It seemed to install no problem.

Regards

Fenris

---

### Post by Orlsend on 2009-03-15
Did it ever pronpt you for the user password?

---

### Post by Fenris_rising on 2009-03-15
Hi there

Yes it asked for the password then the progress bar 'progressed'
but nothing changed.

OS HH 8.04

Python 2.5.2 is the installed version

Compiz is running if this is relevant

Here is the output of terminal whilst using Epidermis 0.2.2 deb

```
fenris@Odhinn:~$ epidermis
Epidermis, Copyright (C) 2008 David D Lowe
Epidermis comes with ABSOLUTELY NO WARRANTY; for details click on the About button, License
This is free software, and you are welcome to redistribute it
under certain conditions; for details click on the About button, License
/usr/lib/python2.5/site-packages/epidermis/epidermis.py:300: GtkWarning: gdk_window_set_icon_list: icons too large
  self.win.show_all()
python: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
fenris@Odhinn:~$ 
```

I uninstalled the epidermis deb package and installed the source tar.gz version 0.2.2
There was an error during install however. Here is the terminal output of the debug.

```
Traceback (most recent call last):
  File "/usr/bin/epidermis", line 14, <module>()
        else:
            import epidermis.epidermis
            epidermis.epidermis.main()
  variables: {'epidermis': (None, None)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 53, <module>()
    import socket #, urllib
    import loadrepo, managepigments
    import ep_exceptions
  variables: {'loadrepo': (None, None), 'managepigments': (None, None)}
  File "/usr/lib/python2.5/site-packages/epidermis/loadrepo.py", line 15, <module>()
    import httplib, urlparse, urllib
    import managepigments
    from glob import glob
  variables: {'managepigments': (None, None)}
  File "/usr/lib/python2.5/site-packages/epidermis/managepigments.py", line 20, <module>()
    import ep_exceptions
    import shell
  variables: {'shell': (None, None)}
  File "/usr/lib/python2.5/site-packages/epidermis/shell.py", line 12, <module>()
    import gtk
    import pexpect
    import os, sys
  variables: {'pexpect': (None, None)}
ImportError: No module named pexpect

debuginfo.debuginfo error
```

I have now uninstalled the tar.gz and have the deb package back in place.



regards

Fenris

---

### Post by Orlsend on 2009-03-15
Sadly I barely know Python, My Place In Epidermis is packaging themes and pigments.

Though I am going to fill in this 2 reports (In Launchpad), Flimm (The red head Mastermind behind Epidermis) should get to them Pretty soon.

BTW I like your Quote, today when I was washing dishes by my self out no where I started quoting it. :D

---

### Post by Fenris_rising on 2009-03-15
Cheers Orlsend I shall wait for your 'partner in crime' :D

That 'quote' was used in PC world Swindon by my good self :D

It's my Mantra :D :D

regards

Fenris

---

