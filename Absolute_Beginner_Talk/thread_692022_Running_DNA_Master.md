---
title: "Running DNA Master"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2008-02-09
I want to run this program in WINE: [http://cobamide2.bio.pitt.edu/](http://cobamide2.bio.pitt.edu/) (Software->DNA Master)
but Ii get funny error messages. Can someone help me run this?

---

### Post by lswest on 2008-02-09
can you post the error message?  need a bit more information

---

### Post by DutyDuty on 2008-02-09
```
This product needs at least 800x600 Resolution.
Setup cannot continue.
```

I don't know how to change the WINE resolution; my normal resolution is far higher.

---

### Post by lswest on 2008-02-09
if you give in ```
winecfg
``` in a terminal, you can, under desktop i think, set it up so it emulates a windows desktop at resolution 800x600.

---

### Post by DutyDuty on 2008-02-09
I can't seem to resize the WINE window to find the "apply" button, since the setting I changed didn't apply itself. How do I make the window smaller/larger?

---

### Post by lswest on 2008-02-09
which window are you speaking of?  the configuration menu? if you hold alt and drag the window up the apply button should come into reach^^

---

### Post by DutyDuty on 2008-02-09
I speak of the WINE desktop. I can move the window, but not very far since the desktop is a tiny box.

---

### Post by lswest on 2008-02-09
you can try different resolutions for the desktop, but you have to set them in winecfg.  Depending on your screen resolution you might want to make the desktop wider and shorter?

---

### Post by DutyDuty on 2008-02-09
I want a larger desktop, since I have barely enough room to move right now. Problem is, I can't set any winecfg settings as I can't access the apply button without a larger desktop, as it is currently about the size of a new post box on these forums.

---

### Post by DutyDuty on 2008-02-09
scratch that. I stabbed in the dark and hit my target, so to speak. I'll post back in DNA Master fails.

---

### Post by lswest on 2008-02-09
ah, i know what you're referring to now, hmm...not sure how to change it, forgot that the winecfg window pops up in the desktop after you set it up.  Can you hit "accept" with <alt>+a?

---

### Post by DutyDuty on 2008-02-09
I ran it and it installed. He's the new error: ```
Exception ElnOutError in module DNAMas.exe at 00351C3E File not found
``` Closes as soon as I hit Ok.

Also, terminal says this twice: ```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

```

---

### Post by lswest on 2008-02-09
do you have your ATI card drivers installed?

also, the first error implies a file is missing, does the program require a certain dll file? if it does, you can copy that file over from a windows install.

---

### Post by DutyDuty on 2008-02-09
I've got every driver I've needed over the past year installed, I'm not sure what you mean exactly though. Also, I don't know how to move that file from a windows install or what I would do with it if I did.

---

### Post by lswest on 2008-02-09
yeah, the thing is, the .exe you have, it's telling you that the exe file is missing a different file, not which one.  Sorry, but i can't help you with this error, it's over my head.  Maybe someone else has some experience with this?

---

### Post by smmalis on 2008-02-12
This is an old thread, but I had the same problem under XP recently.  The problem was it was missing a folder that it couldn't create (for whatever reason).  Create an Archives folder in the program directory and that should fix it.

---

