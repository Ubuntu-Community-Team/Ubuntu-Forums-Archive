---
title: "[SOLVED] iPod managing on ubuntu"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by itix on 2007-12-16
Ok, so here's the thing: Over Christmas (while having access to my brothers gigantic hard drive) I'm getting rid of my windows partition. I just removed the designed for windows xp-emblem and put it on my cellular phone. I have managed to replace all windows functions but one; managing the iPod.

I still haven't figured out any way to managaing my music and video on to my iPod from Ubuntu. Anyone who knows anything about this?

---

### Post by Squizz on 2007-12-16
Use the iPod updater in windows to restore your ipod to factory settings.

Download Rhythmbox or Amarok from add/remove programs.

Import your music library to them, and drag and drop onto your ipod.

Both of the programs are very similar to iTunes, so you shouldn't have many problems.

---

### Post by mpince on 2007-12-16
~

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

---

### Post by itix on 2007-12-16
There was a thread about the subject?? I searched but found nothing...
I'll try rythmbox. I hate amarok. It doubled every song in my library and nothing really worked etc. I use Exaile right now, but it's so early in development, and the iPod-plugin for it just recently got over version 0.1...

---

### Post by Keith Hedger on 2007-12-16
use gtkpod or dump the apple software completly and install rockbox

---

### Post by itix on 2007-12-16
Now this is strange: I was 100% sure that I had gtkpod isntalled. I thought it was just a library to help other applications manage the iPod. Exaile claimed to need gtkpod to sync with iPods.

---

### Post by itix on 2007-12-16
Wohoo.. Gtk-pod works like a charm. Thanx. Goodbye windows.
I won't be seeing it again untlil I've gained enough to buy a mac pro and installed bootcamp on it.

---

### Post by thelatinist on 2007-12-16
> **itix said:**
> Wohoo.. Gtk-pod works like a charm. Thanx. Goodbye windows.
I won't be seeing it again untlil I've gained enough to buy a mac pro and installed bootcamp on it.

Once you have a Mac, why bother?

---

### Post by itix on 2007-12-16
Because you can play windows games on it :p
Sure, I have a ps3, but not all game developers are so intelligent that they realize the superiority of the ps3 contra the windows PC.

---

### Post by da protagonist on 2008-02-24
gtk pod doesn't load my wma files,  What can I do?

---

### Post by LuisGMarine on 2008-02-24
If I were you give banshee a try.  So far its awesome at adding songs automatically when they drop into my music folder, and synchronizes the ipod as soon as its hooked up.  It also doesn't load double songs to your music library.  I can sit there and dump the same folder with the same songs over and over and it will never add duplicates for songs.

Give it a try

```
sudo apt-get install banshee
```

---

### Post by Keith Hedger on 2008-02-24
> **da protagonist said:**
> gtk pod doesn't load my wma files,  What can I do?
Use rockbox, the apple firmware wont play wma's so gtkpod wont try and load them into your ipod.

---

