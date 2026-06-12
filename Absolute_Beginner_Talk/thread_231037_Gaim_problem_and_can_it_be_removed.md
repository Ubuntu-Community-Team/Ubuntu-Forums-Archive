---
title: "Gaim problem and can it be removed?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-08-06
gaim will sign off while appearing to still be running and it shows no sign of problem. i can move it around, instant message people and everything, but no one gets my messages and to them, i'm signed off..the only way i can tell it's messed up is to exit gaim and it'll ask me to force quit..any idea?

i attempted to remove it and try to reinstall it, but i didn't want to remove the entire ubuntu-desktop. when i "reinstall" it doesnt do anything to correct the problem.

---

### Post by batholith on 2006-08-06
I don't do much instant messaging, but I know from other programs, uninstalling "ubuntu-desktop" is not that big of a deal...it's easily reinstalled.  It doesn't hose your computer or anything (at least not in my experience).

I had to do a similar task to fix some sound problems on Dapper.  Just type the following into a terminal window after you remove and reinstall Gaim and you should be set...


$sudo apt-get install ubuntu-desktop

---

### Post by ewl1217 on 2006-08-06
Don't worry aobut removing the ubuntu-desktop package. All it is is just a meta-package to make installing the basic desktop easy, and to ease updates (so you get any new software added to Ubuntu). You can remove it temporarily or even permanently with no harm.

---

### Post by shanepardue on 2006-08-07
i removed it and reinstalled and the same problem occurs..any ideas?

---

### Post by cazique on 2006-12-18
gaim seems quite buggy! why not try aMSN! works nice with me! :) 

sudo apt-get remove gaim
sudo apt-get install amsn

---

### Post by Pobega on 2006-12-18
> **cazique said:**
> gaim seems quite buggy! why not try aMSN! works nice with me! :) 

sudo apt-get remove gaim
sudo apt-get install amsn

Gaim also covers multiple clients, which is something amsn doesn't do.

Gaim used to do this to me on Windows all of the time, maybe try reinstalling GTK? That's how I fixed it on Windows...Not sure if that's even applicable to Ubuntu/Linux.

---

