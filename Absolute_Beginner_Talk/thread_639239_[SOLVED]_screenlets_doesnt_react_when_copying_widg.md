---
title: "[SOLVED] screenlets doesnt react when copying widgets to folder"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by lanchongzi on 2007-12-13
I installed screenlets in Ubuntu 7.10 ( had to download it - don't remember the source I guess it was screenlets.org ) the basic screenlets (the one that come with it) work perfect 
Now when I download Desklets and put them in either /usr/local/share/screenlets or in /.screenlets ( using gksudo nautilus to drag and drop ) the screenlets manager doesn't start anymore? only untill I delete the just copied files it will work again
also when i install within the managerit tells me "Invalid archive. Archive must contain a directory with the screenlet's name."

what is it I am not getting here?


Thanks in advance

---

### Post by sourcemorph on 2007-12-13
well in terminal change ur working directory to /usr/local/share/screenlets .. extract the screenlet folder from the tar.gz file you downloaded into this directory.. then do this (eg. you wanna start the nowplaying widget).

```
user@host:/usr/local/share/screenlets$ cd Playing/
user@host:/usr/local/share/screenlets/NowPlaying$ ./NowPlayingScreenlet.py 
```

this will start the widget, close it. now when u'll open the screenlets manager it'll show it in the list.

---

### Post by lanchongzi on 2007-12-13
solved my problems by overriding the screenlet-0.0.10 with screenlet-0.0.7

but thanks for you reply :)

---

