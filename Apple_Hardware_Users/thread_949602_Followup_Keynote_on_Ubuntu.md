---
title: "Followup: Keynote on Ubuntu"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by Traumflug on 2008-10-16
Hello all,

I just googled for a iWork Keynote replacement for Ubuntu and found a post so wrong I can't resist to comment this. Unfortunately, it's in a read-only Froum, so I have to report here:

[http://ubuntuforums.org/showthread.php?p=3803234#post3803234](http://ubuntuforums.org/showthread.php?p=3803234#post3803234)

[quote="gubemton"]The impossibility of porting Mac Software to Linux relies not in the architecture but in the graphics management or window manager.[/quote]
Pardon. It's neither impossible to mix more than one graphics environment in Ubuntu nor is there any restriction to port Mac software to Linux. Even a Cocoa-like graphics environment exists already: [GNUstep](http://www.gnustep.org).

Even if there weren't GNUstep, it would still be possible to clone Keynote's appearance and behaviour with Gnome, Qt, whatever. The unique thing about Mac software isn't some hidden secret, it's about making the GUI simpler, yet more functional. Mac fans love the way Macs work, Linux fans obviously prefer less intuitive, more feature-rich (cluttered?) applications. That's all.

> So it's not that simple. And so iwork is not open source...
You're correct in iWork nor being open source, but the only reason for this is, Apple doesn't want to release it under such a license. That's all and there's nothing stopping an enthusiastic programmer from crafting something with an iWork-like user interface, reading and writing iWork-compatible files.


Cheers,
Traumflug

---

### Post by Ub1476 on 2008-10-16
Here's an app which has nice eyecandy at least:

[http://sliderocket.com/](http://sliderocket.com/)

---

### Post by cyberdork33 on 2008-10-16
> **Traumflug said:**
> That's all and there's nothing stopping an enthusiastic programmer from crafting something with an iWork-like user interface, reading and writing iWork-compatible files.
I eagerly await your application.

---

### Post by jwhendy on 2008-10-23
If anything actually gets done with this, I think a start would be simply to be able to convert files from one format to another. One benefit is that at least Apple uses xml format for the storage of document data, styles, formats, etc. One can look at these pretty easily, and while it would be a long process to back-engineer all of the tags, it would definitely be possible to then create some sort of exporter/importer.

I don't know what the format for word, excel, and powerpoint docs are (as in something encrypted, coded, etc...). I suppose one could look at OpenOffices code and how it converts to MS Office formats and modify it to work with iWork?

I'm going to further look starting with an iWork Pages document with just text to see what I can figure out. Anyone else interested in actually trying something with this idea? An iWork to/from ODF/MS Office converter would prove very useful!


-John

---

