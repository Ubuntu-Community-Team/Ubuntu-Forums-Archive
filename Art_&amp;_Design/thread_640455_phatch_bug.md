---
title: "phatch bug"
date: 2007-12-14
forum: Art &amp; Design
---

### Post by frinux on 2007-12-14
Hi,
I'm testing phatch now, and think it is a great software. Allthough, I'm encountering a bug with the Watermark function : when I try to use it, i get this error in the command line :

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/phatch/pyWx/gui.py", line 253, in on_menu_tools_execute
    base.apply_actions(self.tree.export_forms(),self.settings)
  File "/usr/lib/python2.5/site-packages/phatch/core/base.py", line 301, in apply_actions
    stop_for_errors)
  File "/usr/lib/python2.5/site-packages/phatch/core/base.py", line 229, in apply_action
    stop_for_errors,ignore)
  File "/usr/lib/python2.5/site-packages/phatch/core/base.py", line 202, in process_error
    details = log_error(message,details,image_file,action)
  File "/usr/lib/python2.5/site-packages/phatch/core/base.py", line 69, in log_error
    'Details: "%s"'%details,
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 38: ordinal not in range(128)

Here is my configuration:
Kubuntu 7.10
Kernel 2.6.22-14
Phatch 0.1.bzr172
python-wxgtk2.8

Is it a software bug, or is it coming from my configuration ?

---

### Post by stani on 2007-12-20
Just to notifiy other people, bugs should always get reported on launchpad. You can follow this bug at:
[https://bugs.launchpad.net/phatch/+bug/176359](https://bugs.launchpad.net/phatch/+bug/176359)

According to me, it is fixed now with the latest version which can be downloaded at [http://photobatch.stani.be](http://photobatch.stani.be)

---

