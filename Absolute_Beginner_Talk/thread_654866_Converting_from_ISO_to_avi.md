---
title: "Converting from ISO to avi"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Squizz on 2007-12-31
Hi there,

I'd like to convert a movie from bin/cue format to .avi or similar so I can stream it to xbox.

I've converted from bin/cue to .iso using bchunk, which has left me with two .iso files.

I can only open/mount one of them, and when I navigate to the biggest file (which I'm assuming is the movie) there's a .dat file there which I don't seem to be able to extract or do anything else with.

Is there a way to do it properly, or preferably something similar to isoBuster?

Thanks very much

edit: I can play the bin file fine in VLC, but not the iso - but I need to have the file extracted anyway.

---

### Post by pt123 on 2007-12-31
if it is a dat file then its is a VCD hence an mpeg file. Why not copy the dat file to a hard disk and rename the extension mpg? 

Then open the file with a program like Avidemux
[http://www.getdeb.net/app.php?name=avidemux](http://www.getdeb.net/app.php?name=avidemux)

This should not be in beginners talk.

---

### Post by (((X))) on 2007-12-31
You can burn it as an ISO, then you can copy your .avi to your computer from burned cd..

---

### Post by Squizz on 2008-01-01
> **pt123 said:**
> if it is a dat file then its is a VCD hence an mpeg file. Why not copy the dat file to a hard disk and rename the extension mpg? 

Then open the file with a program like Avidemux
[http://www.getdeb.net/app.php?name=avidemux](http://www.getdeb.net/app.php?name=avidemux)

This should not be in beginners talk.

As I said, I don't seem to be able to extract the .dat file.  I've mounted it and gone in via the gui and also tried to sudo mv it.

And I put it in beginners talk, as the process is very simple in Windows and I couldn't find anything on the forums here that could help.

[QUOTE=(((X)))]
You can burn it as an ISO, then you can copy your .avi to your computer from burned cd..
[/quote]

That would be the same as mounting it, but you'd lose a CD in the process.

---

### Post by bigken on 2008-01-01
you could try Gmount-iso

---

### Post by Squizz on 2008-01-01
> **bigken said:**
> you could try Gmount-iso

That tool is awesome thanks - although I still couldn't get that pesky .dat file out.

It throws the error

```

Error "I/O error" while copying "/media/cdr...vseq01.dat"

```

---

### Post by bigken on 2008-01-01
dont know if [this ]("http://www.mail-archive.com/linux-india-help@lists.sourceforge.net/msg36735.html")will help

---

### Post by Squizz on 2008-01-01
Yeah, that looks like it could be the culprit - shall have to try and work around it though - thanks for your help :)

---

