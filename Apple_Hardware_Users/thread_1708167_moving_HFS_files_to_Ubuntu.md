---
title: "moving HFS files to Ubuntu?"
date: 2011-03-16
forum: Apple Hardware Users
---

### Post by davidfeldman on 2011-03-16
I'm replacing my old PowerBook file/print/backup server with an Ubuntu Atom-based one. As such I'm trying to bring over the old files -- ideally my CrashPlan backup archive, but more importantly about 150GB of archived documents of various types. Many are old enough to rely on HFS+ metadata and resource forks.

What's the best way to do this? Should I leave them on HFS+ and use Ubuntu's built-in HFS support? Or should I copy them over to ext4, in which case what's the best way to do that without losing data (especially the metadata and resource forks)?

Thanks!

---

### Post by davidfeldman on 2011-03-18
Anyone? A little help over here...

---

### Post by rg4w on 2011-03-18
It's the resource forks that are most problematic.  What type of documents are they?

In many cases the res fork includes relatively minor data.  For example, with the old TextEdit apps, its documents were plain text files, but if you used styled text in them the style runs were stored in the resource fork.  So if you opened the file in any editor that doesn't understand res forks, you'd get just the plain text without formatting, but at least the text would be there intact.

---

### Post by davidfeldman on 2011-03-18
To be honest I'm not entirely sure. The folder is my archived files going back to 1988. There's some SuperPaint in there, whatever non-Word word processor we were using at the time, dunno what else in terms of non-standard stuff. Probably some old apps but those won't run anyway.

Certainly the simplest thing to do would be leave it as HFS+ since Ubuntu can read/write it. But I get the sense that might not be as safe a long-term option?

---

### Post by rg4w on 2011-03-18
I'm no expert on file systems so I'll leave that to the smarter folks here.

But for getting data out of older Mac apps you might consider SheepShaver:
[http://sheepshaver.cebix.net/](http://sheepshaver.cebix.net/)

SuperPaint files will be a difficult task to attempt with any other program, since their then-groundbreaking integration of raster and vector graphics required them to use a file format almost nothing else can understand.  That said, SP has a wide variety of export options, so if you can run it under SheepShaver you may be able to export to EPS or some other common transfer format for use in modern apps.

---

