---
title: "making a shortcut"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by elpichi on 2007-05-24
Alright this is my problem:
i have 2 hard drives, one with ubuntu and one with windows, now i was thinking of a way to make it easier to access the files in my windows partition by making a shortcut on the desktop taking me straight to my documents just like a shortcut

i was thinking doing a launcher that would open up file browser addressing to My Documents, the problem is i don't know the command to open the file browser and to address it to /media/disk/documents and settings/owner/my documents

if there is an easier way or if its possible a direct link to that folder from the desktop =\

thanks in advance

---

### Post by spin2cool on 2007-05-24
You're looking for the 'ln' command.  Something like this would do the trick

ln -s /media/disk/documents ~/Desktop/documents

Links are better in many respects than windows shortcuts, because you can browse down through folders and stuff as if the files really existed on your desktop.

---

### Post by elpichi on 2007-05-24
uff exactly what i needed, thanks

---

### Post by bobrektasi on 2007-05-24
select file and, drag-and-drop  with ctrl+shift

---

