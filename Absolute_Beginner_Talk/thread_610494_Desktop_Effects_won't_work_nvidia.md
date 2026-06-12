---
title: "Desktop Effects won't work nvidia"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by diec23 on 2007-11-12
When I enable desktop effects with my nvidia Geforce GO 7600 (drivers installed) the windows lose their maximize/minimize buttons and generally become unmovable.  What can I do to fix it?

---

### Post by bulldog on 2007-11-12
Install a package called emerald from synaptic.

---

### Post by diec23 on 2007-11-12
> **bulldog said:**
> Install a package called emerald from synaptic.

Hrm, that didn't work

---

### Post by diec23 on 2007-11-12
Notice the lack of [x] or [-] at right top of window

---

### Post by ant2ne on 2007-11-12
64bit cpu? Ruined my day.

---

### Post by marsmissionaries on 2007-11-12
open a terminal and type "compiz --replace" and post the output. also try "emerald --replace"

---

### Post by diec23 on 2007-11-12
> **marsmissionaries said:**
> open a terminal and type "compiz --replace" and post the output. also try "emerald --replace"

Yikes:

"inotify_add_watch: No such file or directory
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32"

---

### Post by alienexplorers on 2007-11-12
Are you sure you are running the restricted drrivers for your nvidia card.

---

### Post by bulldog on 2007-11-12
> **diec23 said:**
> Yikes:

"inotify_add_watch: No such file or directory
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32"

You have to set the depht 24!
You should do this in xorg.conf.
Make a safety copy first,
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Now to edit xorg,
```
gksu gedit /etc/X11/xorg.conf
```
Change the default depht into 24

---

### Post by diec23 on 2007-11-12
> **alienexplorers said:**
> Are you sure you are running the restricted drrivers for your nvidia card.

No, how do I know this?  I installed via automatix.  Geforce Go 7600

---

### Post by inversekinetix on 2007-11-12
Make sure you go into the Emerald Theme Manager and choose a them to use.  its in System >>>

---

### Post by diec23 on 2007-11-12
> **inversekinetix said:**
> Make sure you go into the Emerald Theme Manager and choose a them to use.  its in System >>>

I did this, but it doesn't change my theme...I select it, but nothing happens.

---

### Post by diec23 on 2007-11-12
> **bulldog said:**
> You have to set the depht 24!
You should do this in xorg.conf.
Make a safety copy first,
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Now to edit xorg,
```
gksu gedit /etc/X11/xorg.conf
```
Change the default depht into 24

Default depth is already 24

---

