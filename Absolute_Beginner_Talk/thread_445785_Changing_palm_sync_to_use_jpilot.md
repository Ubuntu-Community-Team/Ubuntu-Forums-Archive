---
title: "Changing palm sync to use jpilot?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-05-16
If I hit the hotsync button on my Palm while connected by USB it will attempt to sync with Evolution, however I use jpilot.

Is there a way to change this behavior?  I figure it has to do with modifying a udev rule but I don't really know where to start with that.

I do know that the command to sync with jpilot is```
jpilot -s
```  How would I go about finding out what rule to create/modify?  An answer is nice, but an explanation would be better so I can figure these things out in the future.

Thanks.

---

### Post by aroch1 on 2007-05-17
Try System->Preferences->Removable Drives and Media->PDAs.

This dialog will let you modify the program called when you plug your palm in...I don't know if this is also the program that is called when you press the sync button, but its easier than editing a udev file and it's worth a shot.

---

### Post by lazyart on 2007-05-17
wow, is it that simple?  thanks. :)

---

### Post by ChrisC on 2007-08-05
Boy, it sure would be nice if this command line option:
```
jpilot -s
(thanks lazyart)
```
... was mentioned in the JPilot docs.

I have my Palm interfaced via serial ( /dev/ttyS0 ), but this is not working, even though I have set the pref.  Does anyone have their SERIALLY-INTERFACED Palm working with JPilot such that it syncs after you push the hotsync button on the device?

Currently I have to press/click the HotSync button on both sides to get it to go.

---

### Post by Robin50 on 2007-12-18
I'm having the same problem, I want to sync a palm tx with jpilot, not evolution as it does currently. It seems I need to install conduits in the gnome pilot but I'm 1 week old with ubuntu and it's a bit beyond me. I get the following error message when I push the sync button - 

pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Would really appreciate some help here, thanks in advance

---

