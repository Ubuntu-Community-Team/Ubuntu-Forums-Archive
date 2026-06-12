---
title: "Mild Slowing Down In Speed"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by wdbreen on 2006-04-28
Hello Linux Community.
I've been running Breezy for a couple of months now and love it (Wont ever be going back to windows!) but my machine is starting to show signs of slowing down i.e.  windows opening up slower, firefox a little more sluggish.

Since i have been trying a lot of the repository software to find what i like (and then removing them if dont), does this leave behind a lot of files and folders in the /home and /usr directories? and what else do you think might do this?

Thanks in advance

---

### Post by louis_nichols on 2006-04-28
Well... one difference between Linux and windows is that, from one startup to the other, Linux runs the same way. It doesn't have a registry database that becomes over-crowded, fragmented and corrupted, slowing the system down. Any files and folders left behind by installing/uninstalling (which doesn't happen that much) stuff shouldn't affect your system unless something extreme happens, like your partition becoming full.

Try to think of other changes you may have made: software that runs various services all the time, or extra eye-candy. Perhaps changing settings for X, or disabling the video drivers or dma settings for your optical drives. It's changes like these that can slow dwn the system, rather than simply installing/uninstalling stuff, which is pretty safe.

---

### Post by pbaehr on 2006-04-28
I would pay extra attention to anything you installed which is running all the time. I had a problem where something was hogging my processor more and more the longer the computer was on. I traced it back to a simple little gdesklet that counted down to a set time. Once I took it off everything went back to normal.

---

