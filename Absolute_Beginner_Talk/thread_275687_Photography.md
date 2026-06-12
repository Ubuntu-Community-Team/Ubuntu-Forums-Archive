---
title: "Photography"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-10-11
I'm new to Linux so pardon me if this is a dumb question.  I have a few normal size pictures that I wan't to make into one large panoramic picture.  I have been able to do this before in a windows program, but I'm not sure if there is a program like that in Linux.  If there is, what is it, and how do I go about combining the pictures?  Thanks for your help.

---

### Post by gn2 on 2006-10-11
> **CeeDub said:**
> I'm new to Linux so pardon me if this is a dumb question.  I have a few normal size pictures that I wan't to make into one large panoramic picture.  I have been able to do this before in a windows program, but I'm not sure if there is a program like that in Linux.  If there is, what is it, and how do I go about combining the pictures?  Thanks for your help.

It should be possible with the Gimp?

---

### Post by CeeDub on 2006-10-11
I've been looking around in the Gimp, but I haven't seen anything I can use.  I'm not much into graphics and what now, so Gimp is a little confusing for someone new to it and not really wanting to put much effort into learning it.  Is anyone out there a guru in this sort of thing that can help out?

---

### Post by fragos on 2006-10-11
You might try openoffice writer.  You can insert pictures and anchor them to the page which will let you move them around.  Resizing an image is also easy, just grab a corner and move.

---

### Post by bodhi.zazen on 2006-10-11
gimp will do this no problem.

Tutorial: [Gimp How to make Panoramic Images](http://www.linuxjournal.com/comment/reply/7295)

---

### Post by Marsolin on 2006-10-12
[Hugin]("http://linuxappfinder.com/package/hugin") is a designed specifically for sticking photos together to create a panorama view.

[Pandora]("http://linuxappfinder.com/package/pandora") is a plug-in for [Gimp]("http://linuxappfinder.com/package/gimp") that will do the same thing.

---

### Post by DarkN00b on 2006-10-12
You could try [XNview]("http://www.xnview.com/"). It has a "Create Panorama" batch option. It is not in the repos though I wish it was. It is my favorite image viewer, very similar to Irfanview. The Linux binary is available at the above link, and available in many languages. You can read and write to so many different formats, some I've never even heard of.

Anyway, maybe it'll do what you need.

---

### Post by towsonu2003 on 2006-10-12
try [http://www.cs.ubc.ca/~mbrown/autostitch/autostitch.html](http://www.cs.ubc.ca/~mbrown/autostitch/autostitch.html)

it runs nicely with wine, and it is the BEST stitching programs I have ever encountered. you do nothing. it takes care of everything for you... amazing!

```

unzip autostitch.zip
wine ./autostitch.exe
```
and follow onscreen steps. the image it creates will drop to the same directory where your images are, and its name will be pano.jpg...

---

### Post by towsonu2003 on 2006-10-12
by the way, the only thing I *hate* in autostitch is:

> The version of Autostitch on this website is a demo only. Individuals or companies are free to use images that they generate using the demo version of Autostitch without restriction or royalties so long as they acknowledge the use of Autostitch in such works. A commercial license to Autostitch provides access to the patent, source code, technical support and updates

of course, one could [**contact the author**]("http://www.cs.ubc.ca/~mbrown/contact/contact.html") to release the source code with gpl... but one would need very strong arguments...

---

