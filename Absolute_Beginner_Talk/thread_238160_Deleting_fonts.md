---
title: "Deleting fonts"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by letsgofishing on 2006-08-17
Hi there fellow newbies!
I've just installed Dapper Drake and evrything is up and running.!!! I've got Inkscape and Scribus installed (I'm a graphic designer) butthe stock fonts are awfull. I found a folder called fonts under my Home folder. (had to check "show hidden files and folders") The "standard" fonts aren't in there. I copied all my windows True Type fonts over and they all work fine.
I'm just trying to find where the standard fonts are stored so I can delete most of them.
Many thanks,

---

### Post by noynac on 2006-08-17
You can use Synaptic to uninstall fonts. Open Synaptic and do a search for fonts or truetype.

You can view the actual font files with Nautilus by typing fonts:/// in the location bar. 

noynac

---

### Post by liquid06 on 2007-11-25
I have a related question - how do I delete the locked font files?  The error message talks about how I don't have permissions to delete the files.  How do I tell the system that I am the owner?

Many thanks from a lost n00b!

---

### Post by jordanmthomas on 2007-11-26
```
gksudo nautilus fonts:///
```
Be careful though, because I think some programs expect certain fonts to be there.
Also, be careful because you'll be running this as root, and can delete ANYTHING on your system.  <-- read that twice.

---

