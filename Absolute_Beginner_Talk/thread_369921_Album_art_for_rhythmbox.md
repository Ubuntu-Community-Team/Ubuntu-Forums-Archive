---
title: "Album art for rhythmbox"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by benhall on 2007-02-25
Hi

Sorry for asking such a simple question, but how do I add album art to rhythmbox? I know it can play it- when I transfer albums from an ipod with art to my laptop I see it come up, but I can't find an option to add art. I'm probably missing something easy, but I would appreciate some help

Many thanks

Ben

---

### Post by kevinlyfellow on 2007-02-25
Go to edit -> plugins.  Check the appropriate box

---

### Post by benhall on 2007-02-25
The plugin is selected- I just can't find a tab or option to add album art to a given album. If I add the music from a source where it is associated with art (the above ipod) the art is added automatically, I just can't add it manually.

---

### Post by benhall on 2007-02-25
Ok, well I found that disabling and enabling the plugin made it start picking up the covers automatically. I still can't find a GUI to add art manually, but I think the plugin will pick up a graphic if it is present in the albums folder as a jpg whose name is one of the following:

> IMAGE_NAMES = ["cover", "album", "albumart", ".folder", "folder"]

Thanks for the advice

Edit:

If artwork has already been selected you may need to remove it from the ~/.gnome2/rhythmbox/covers/$artist-$album. You can also copy downloaded art to where the incorrect art is here.

A GUI for this would be helpful. I don't know if it would be hard or easy to code into the plugin, but I'll have a look.

---

### Post by mgmiller on 2007-04-28
Try installing easytag.  It lets you modify anything in the id3 tag including adding art.  I guess you would modify the mp3 on your hard drive and then synch it back to the ipod.

---

