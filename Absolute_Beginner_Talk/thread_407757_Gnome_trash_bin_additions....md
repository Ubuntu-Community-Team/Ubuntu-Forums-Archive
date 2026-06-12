---
title: "Gnome trash bin additions..."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by TehSnarf on 2007-04-12
Alright, so.. I think I'm almost fully converted (woo) from Windows to Ubuntu.. just a few more tiny things and such. I was wondering, is there a way to make the Gnome Trash applet monitor other .Trash folders on other hdds?

Basically, my setup is this:
hda = /media/WinXP (50 Gig)
hdb = /media/Storage (300 Gig)
hdd = Ubuntu (6 Gig)

I noticed that if I put something from either one of the NTFS drives (/media/Storage or /media/WinXP), my trash applet in my panel doesn't show that there's anything in the trash. After some investigating, I think I've figured out the reason is Ubuntu moves it to a .Trash-$USER folder on the drive itself, so since I trashed /media/Storage/FILE it gets moved to /media/Storage/.Trash-ME/FILE ... which is fine with me, since some of the files I'm going to be removing are fairly large, and I really don't see a point in transferring them from one drive to another.

Sure, I can go into any of the .Trash folders and manually remove them, which I'm perfectly content with, but I'm not done tinkering!

---

### Post by igknighted on 2007-04-12
If you hold shift and press delete it will permanently delete the file, no trash involved... is this what you are looking for?

---

### Post by TehSnarf on 2007-04-12
More like... add to the applet monitor other .Trash folders to also "monitor"

---

