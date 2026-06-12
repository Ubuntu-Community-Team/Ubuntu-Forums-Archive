---
title: "rm -r python-setuptools, Now I'm in trouble"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by dwdarkstar on 2008-02-16
Hey,  i spent the day trying to install Jokosher on my drapper system.  After downloading and unpacking the file, the configuration failed because of a missing dependency related to python.  After enabling all repositories and reloading Synaptic the needed file was no where to be found.  So i went and got it.  Installing this required that, and so on and so on until frustration got the better of me and i rm -r python-setuptools after it failed to install.  Now when I open Synaptic i get this error message:

E: The package python-setuptools needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

And if i search for python, there is NOTHING!!!  this morning i had thousands of packages related to python.  Worse, my gui interface is breaking down, folders won't open.  I downloaded python-setuptools but easy_install gives me this:

farstar@farstar-laptop:~/Desktop$ cd setuptools-0.6c3/
farstar@farstar-laptop:~/Desktop/setuptools-0.6c3$ easy_install
Traceback (most recent call last):
  File "/usr/bin/easy_install", line 5, in ?
    from pkg_resources import load_entry_point
ImportError: No module named pkg_resources
farstar@farstar-laptop:~/Desktop/setuptools-0.6c3$

All this so i could edit a 3 second clip of R2D2 into a custome ringtone for my choclate.

I don't know what to do, and that error message scares me.  HELP

---

### Post by spiderbatdad on 2008-02-16
Why are you still using Dapper? Probably all of that could have been avoided with the latest release. For example, synaptic and gDebi now provide the dependencies for you, if they are available. Why not save any files you want, burn a fresh copy of 7.10, and upgrade. Would be best to have a P4 or better and 512 RAM.

---

