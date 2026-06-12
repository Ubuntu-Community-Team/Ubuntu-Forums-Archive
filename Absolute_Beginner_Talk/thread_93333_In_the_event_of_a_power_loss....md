---
title: "In the event of a power loss..."
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by dpack on 2005-11-21
I leave my PC running all the time. If I had a power loss while running Windows, I just booted the PC back up being that I was using NTFS file system. If something did act goofy, I would schedule a chkdsk on next reboot. Now I am running Ubuntu using ext3 file system. If I experience a power loss, are there any system utilities that I need to run to check things out and make sure everything is okay?

Thanks!
David

---

### Post by matthew on 2005-11-21
The answer is "yes" and "no." 

There are utilities that should be run after a power loss, but the cool thing is that when you boot an ext3 drive it is quickly and automatically checked by looking at the journal, if there is the slightest hint of an error the whole drive/partition is *automatically* checked.

---

