---
title: "[SOLVED] How can I save stuff from a non booting partition to a flash drive?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-21
How can I do this through a flashdrive in a live cd? I need awnsers please... Thank you all

---

### Post by -gabe-noob- on 2008-01-21
Hmm I think I man have found a way... will post results here

---

### Post by -gabe-noob- on 2008-01-21
Though this is a long and arguos process to get all your files.. .I've DONE IT!!!

What you must do: this is only for OpenOffice.org documents

You open up which ever you may need... (writer spred sheet ect) 

Go to open, then it will say volumex (x being a number) click on that.

Then it will have a bunch of folders

Click on home

then your user name 

then documents

then find whatever you need 

then open it up

then finally save it to the flash disk

---

### Post by az on 2008-01-21
Boot the live cd, insert the USB stick, mount the non-booting partition and then drag-and-drop.

If you can't read the damaged disk, try 

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org).  

Or simply use ddrescue to image the disk to a file (on a bigger disk) and then either try to mount the image as a loop filesystem - then drag-and-drop.  Or data-carve the files if the filesystem is dammaged.

---

