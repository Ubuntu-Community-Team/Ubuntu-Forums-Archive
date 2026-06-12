---
title: "Ubuntu Ctrl+Alt+Delete Equivalent"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-17
What's the Ubuntu equivalent of Ctrl+Alt+Delete?  I haven't figured out how to install my [Nvidia drivers]("http://http://www.ubuntuforums.org/showthread.php?t=217933") yet and I just opened a game that looks pretty dependant on them (it's freezing up alot).  What's worse is it absolutely will not close out.  How do I force it to close?

---

### Post by Silver Streak on 2006-07-17
> **fatsheep said:**
> What's the Ubuntu equivalent of Ctrl+Alt+Delete?  I haven't figured out how to install my [Nvidia drivers]("http://http://www.ubuntuforums.org/showthread.php?t=217933") yet and I just opened a game that looks pretty dependant on them (it's freezing up alot).  What's worse is it absolutely will not close out.  How do I force it to close?

If you can get to a terminal, you can type
```
killall processname
```
where processname is the name of the program. If you know the first part of the process name, you can press TAB, and it may autocomplete it.

Ah, I see that you're having problems with installing the nVidia drivers. Sorry for not reading! :p

SS

---

### Post by junamuno on 2006-07-17
you can either kill it from the terminal or go to System>Administration>System monitor and you can kill it from there, also I would recomend to put the sistem monitor on the top toolbar, I have it next to the clock.

Hope it helps!!

---

### Post by Metacarpal on 2006-07-17
> **fatsheep said:**
> What's the Ubuntu equivalent of Ctrl+Alt+Delete?  I haven't figured out how to install my [Nvidia drivers]("http://http://www.ubuntuforums.org/showthread.php?t=217933") yet and I just opened a game that looks pretty dependant on them (it's freezing up alot).  What's worse is it absolutely will not close out.  How do I force it to close?

If you're running the game in a window (that is, not full-screen) another quick trick is this: right-click your panel, and click "Add to Panel".  In the "Desktop and Windows" section is a button marked "Force Quit".  Choose that and Add.

If any program/window you are running freezes, you can click that icon on your panel, then click the frozen app to force-quit.

---

### Post by crispy_420 on 2006-07-17
But if he if locked into full screen mode would those steps even help?

As far as NVidia drivers, sorry can't help there. I have an ATI 9800 Pro. But just look around these forums. But if it is anything like my ATI drivers, it was just a matter of editing my xorg.conf. I think the drivers are already there, you just have to turn them on. 

Good Luck...

---

### Post by Tim.R on 2006-07-17
If you're using KDE, try using Ctrl + Alt + Esc then clicking on the window you want to quit (or anywhere if it's fullscreen)...

---

### Post by OU812 on 2006-07-18
Try hitting alt+f2. This will bring up the "run application" menu.

john

---

### Post by diepruis on 2006-07-18
You could also try Ctrl+Alt+Backspace. This is only a last resort, however, as it will kill X11 and all processes. You WILL lose all unsaved work.

---

### Post by Sonic Alpha on 2006-07-18
> **fatsheep said:**
> What's the Ubuntu equivalent of Ctrl+Alt+Delete?  I haven't figured out how to install my [Nvidia drivers]("http://http://www.ubuntuforums.org/showthread.php?t=217933") yet and I just opened a game that looks pretty dependant on them (it's freezing up alot).  What's worse is it absolutely will not close out.  How do I force it to close?

Try [Automatix]("http://www.getautomatix.com"), it will install your drivers, and I believe it also gives you ctrl+alt+delete functionality similar to windows (though I haven't tried this bit yet).

---

### Post by fatsheep on 2006-07-18
> **Sonic Alpha said:**
> Try [Automatix]("http://www.getautomatix.com"), it will install your drivers, and I believe it also gives you ctrl+alt+delete functionality similar to windows (though I haven't tried this bit yet).

I just installed it and I must say this is the most useful tool I have encountered as a begginner to linux.  Thanks for the link. :p

---

### Post by Denis on 2006-07-18
When your GUI locks up, I find it easy to press ctrl-alt-F1 to go to your first virtual terminal. Login there and type killall name_of_the_program. To go back to the graphical interface press crtl-alt-F7.

---

### Post by Sonic Alpha on 2006-07-18
> **fatsheep said:**
> I just installed it and I must say this is the most useful tool I have encountered as a begginner to linux.  Thanks for the link. :p

I've found it very useful too, glad to help :)

---

