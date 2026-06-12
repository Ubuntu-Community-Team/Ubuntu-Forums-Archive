---
title: "simple kde question"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-06-27
how do i add a item to the startup menu?i want beryl to run when i start.

---

### Post by Cresho on 2007-06-27
ex.

for kubuntu, crate a conky file in autostart and allow execute file with permission and insert this

#!/bin/bash
sleep 30 && conky;

also use this for nvidia to remember settings to autostart "nvidia-settings -l"

---

### Post by rickycodie on 2007-06-27
so a less hard answer to my question please.  or a more elaborative one, i am new to kde just trying it out.

---

### Post by Cresho on 2007-06-27
file manager allowes you to view your directories.  Under view, allow "see hidden files"  Then go into your home/yourname/.autostart directory and right click and create a new file.  name this beryl.  Now right click on it and see permssions.  click on tab and set permissions to "allow execute" or something in that manner.  now say okay and right click on it and edit with a text editor and add this to it.



#!/bin/bash
sleep 30 && conky;



now you can reboot or log off and log on and watch  beryl run.

---

