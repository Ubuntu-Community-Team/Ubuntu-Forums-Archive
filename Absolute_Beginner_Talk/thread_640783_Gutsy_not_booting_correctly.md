---
title: "Gutsy not booting correctly"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Eyeyseeh39 on 2007-12-14
OK after one or two minor problems I have enjoyed my few days trying out Ubuntu for the first time, that was until this evening when I tried to boot it up.

The splash screen appears and then the logon screen starts but this is then replaced by a blue wallpaper with 5 icons on and a box in the top left hand corner with a star shape in it.

The icons are 40g drive( my other harddrive with win XP on) Floppy, Deleted Items, Home and File System. These all open to folders on my linux harddrive. Other than that there is nothing else no menu bars or anything.

I tried starting in recovery mode and this got as far as the command prompt but Im unsure what to do next.

This happened after I finaly managed to get the updater to work and it downloaded 190 updates last night. It said it had updated successfullybut I guess something has gone wrong.

Im a complete novice with linux so can you tell me what to do now in simple terms, do I need to reinstall Ubuntu again?

 I hope someone knows what has happened and how to fix it.

Cheers

Iain

---

### Post by rsambuca on 2007-12-14
Sounds like you must have installed a different Window Manager.  To get back to the default Gnome Ubuntu Desktop, press Control-Alt-Backspace.  This will restart your XServer, and bring you to the login screen.  On the bottom left hand corner you will see "Options".  Click there and select "Sessions".  Then change to Gnome.  Then login and you should be back to your regular (Gnome) Ubuntu desktop.

---

### Post by Eyeyseeh39 on 2007-12-14
That was an amazing quick reply and here I am back with a working Gutsy.

Thank you so much rsambuca, Im in your debt.

Cheers

Iain

---

### Post by rsambuca on 2007-12-14
I am sure the other Desktop Environment was working to, but you just weren't familiar with it.  Anyways, glad to help out.

---

