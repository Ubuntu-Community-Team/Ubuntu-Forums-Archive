---
title: "[SOLVED] MP3s to disk with insufficient space - stop partial copy how?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-03-24
I'm using Ubuntu for copying songs and podcasts to my MP3 jukebox.

I've noticed that - if there is insufficient space - the file is partially copied rather than not copied at all.

Unfortunately this isn't always apparent when you try playback, and at this point my jukebox just seems to think it's a corrupt file and closes down!

Is there a way (I'm sure there is!) of making Ubuntu only copy files over if it can fit the whole thing?

Thanks!!!!

---

### Post by aysiu on 2007-03-25
The only thing I can think of is using a different file manager. I'm guessing you're using Nautilus? Maybe try Thunar, Konqueror, Krusader, or Rox-Filer... see if the behavior is different in those. 

As for terminal alternatives, I already looked at ```
man cp
``` and it didn't seem to have any flag to force the *cp* command to do what you want.

---

### Post by Frak on 2007-03-25
Konqueror should be able to releive this, it measures space before it writes.

---

### Post by qprfact on 2007-03-25
Thanks - I will try this.

It's a nice idea that Ubuntu is trying to achieve, but unfortunately my MP3 jukebox isn't so keen!!!

---

