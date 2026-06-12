---
title: "Xara cannot import eps files"
date: 2009-12-11
forum: Art &amp; Design
---

### Post by kangyu29 on 2009-12-11
The eps files are exported from Mathematica. I can open them with Gimp, image view, inkscape etc. but not xara. 

The error is:"No filters that were designed for this type of file have been found. The import will continue suing the most compatible filter, although the image may not appear as intended."
After I click OK button, another error pops out: "Invalid line/shape detected".
OK again, it open another tab with "filename.xar" name on it even I was trying to import a .eps file.

I installed xara through "apt-get", synaptics, package file and tar ball separately. None of them can import the eps files.

The first time start the program after a fresh install, it saying something like "cannot find imagemagick" even I found this package in synaptics and installed it.

It also gave errors at start up:

(xaralx:31375): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:31375): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:31375): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:31375): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:31375): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:31375): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed


Any help will be appreciated!:(

---

### Post by Newfoundlander on 2009-12-13
I would import the eps files into Inkscape, save them as svg, and then open them in Xara.

---

### Post by kangyu29 on 2009-12-13
> **Newfoundlander said:**
> I would import the eps files into Inkscape, save them as svg, and then open them in Xara.

Thanks for the suggestion, 

First, Xara suppose to be able to do this "simple" task, at least it is simple to other software.
Plus, I already tried doing this, it didn't work either. Similar error message: "That file is not recognised by any of the installed filters", press OK, nothing happens.

It looks like I don't have ANY filters, how can I manually install all necessary filters?

---

### Post by Newfoundlander on 2009-12-15
> **kangyu29 said:**
> I already tried doing this, it didn't work either. Similar error message: "That file is not recognised by any of the installed filters", press OK, nothing happens.

At first I was going to recommend saving your file as a "plain SVG" as opposed to an "Inkscape SVG".  But I tried saving one of my designs as a plain SVG and Xara still did not recognise it.

Update: in the Ubuntu Software Centre (10.04) there is a plug-in called xaralx-svg which imports SVG perfectly.  I don't recall seeing it in 9.10 but I'm very happy with Xara now.

---

