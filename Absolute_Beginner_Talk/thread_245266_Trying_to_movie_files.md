---
title: "Trying to movie files"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Crash-n-Burn on 2006-08-27
I'm trying to move new gaim icons into 
/usr/share/pixmaps/gaim/status/default

I have 2 questions.

I have all of the new icons which i downloaded from gnome-look in a folder on the desktop, how do I move the contents inside the folder and not the folder itself?

Also I tried to rename the folder to default and move it but it would not let me copy. I get this error 
cmd@CompMD-Laptop:~$ sudo mv -f /home/cmd/Desktop/default /usr/share/pixmaps/gaim/status/
mv: cannot overwrite directory `/usr/share/pixmaps/gaim/status/default'

Thank You,
Jason

---

### Post by reacocard on 2006-08-27
just do a "sudo nautilus" and navigate to /usr/share/pixmaps/gaim/status/default. then just drag the new icons into that window.

---

