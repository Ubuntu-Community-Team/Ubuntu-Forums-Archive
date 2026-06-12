---
title: "repair broken link"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-06
How do you repair a broken symbolic link (soft). I know I could make a new one but if it can be repaired, I'd like to learn how. 

The reason: I changed the mount points of my partitions so they have human readable names like Gadzooks and Factoid.

---

### Post by aysiu on 2007-04-06
So, in other words, you have a symlink from /home/patrick/blah to /media/hda2/blah and you now want the symlink to point to /Gadzooks/blah?

I don't know if a symlink is something you can do a find/replace on, but could you maybe create a symlink from /media/hda2 to /Gadzooks? Would that work?

---

### Post by Patrick K on 2007-04-06
That's correct. That is what I want to change. 

The partition that was once mounted at /media/hda2 is now mounted at /media/gadzooks. The /media/hda2 directory still exist (I haven't deleted it yet) but is empty.  

I'm thinking there isn't a way to do this. I tried opening the link in a text editor but it's a no go. I've done this with Windows links before, using a hex editor, with mixed results. 

I'll just recreate it. Fortunately, I don't have many at this time.

---

