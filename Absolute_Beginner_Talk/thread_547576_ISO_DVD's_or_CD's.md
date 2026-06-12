---
title: "ISO DVD's or CD's?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by jwilson on 2007-09-10
OK, I may seem dumb but whats the trick with the ISO's.
I burn to a DVD but they won't boot. Tried on multiple dvd rom drives-nothing. Cannot burn a 800+ cd to a 700 MB cd ya, got that. Soooooo whats the dealio???? Using Nero 6.5 w/windows to create.

---

### Post by szymon_g on 2007-09-10
did you burned it as a normal data? or as 'cd image file' look in options for something like bourning image files etc (i dont have nero so i cannot tell you exactly name of this option) :-/

---

### Post by BrendanM on 2007-09-10
I always just right click on the .iso and hit "open with nero" and that picks the right type. I think I might have a later version of Nero, though.

---

### Post by szymon_g on 2007-09-10
as i wrote: try to open nero first, then- find in options something like 'burn an image file' or 'burn cd-image' etc, then select a .iso file an burn it :P 
btw, did you checked md5sum of this .iso file?

---

### Post by steve.horsley on 2007-09-10
szymon_g is right. ISO images are a special case - they are an image of a CD including its file system headers and its bootsector. You don't open them and burn the contents to CD as you might a ZIP file. You don't just burn the .ISO file to CD as a large data file. It has to be handled a special way.

There is a special menu option to burn an ISO image to a CD in Nero.

Good luck.

---

