---
title: "how should you deal with a program not resonding?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by h-town on 2007-11-12
I've always been super impatient when it comes to programs not responding and I'd usually ctrlaltdel and end program a few times in windows and if that didn't work in less than 30 seconds I'd manually restart my PC (my gut always told me this is not the correct way to deal with things but I'm pretty casual about worrying about that sort of thing, which I'm sure is the wrong thing to do!) 

So, in case ubuntu (or linux as a whole) really doesn't make nice with that sort of behaviour, what are your thoughts on the correct procedure to dealing with a program not responding??

---

### Post by LaRoza on 2007-11-12
Killing an application is easy. Much better than the Windows way.

If it cannot be stopped, you will get an option to force it to quit, which works like a charm. There are other ways, in the terminal, and with a GUI, but Ubuntu is good about catching them in my experience.

---

### Post by jusmurph on 2007-11-12
Add system onitor to a panel. Double clicking that brings up a menu that allows you to kill processes.

Thats how i deal with it.

---

### Post by wlc3069 on 2007-11-12
I think the best way would be to add a force quit icon to a panel, and when it happens just click it then click the window you want to force quit. Works great, and works instantly everytime.

---

### Post by natehatewindows on 2007-11-12
you can also add the force quit to your panel.  just right click the panel and select force quit and press add. now when a program stops responding you can just press this icon.

---

### Post by h-town on 2007-11-12
thanks for the info!

---

### Post by ant2ne on 2007-11-12
my favorite

```
ps -A | grep nameoftarget
``` *

```
killall  nameoftarget
```

you feel like a ninja with at contract on one special person.

*note: nameoftargert could be just a piece of the name like "k3" of "k3b"

---

### Post by asplodzor on 2007-12-06
I actually just ran into an interesting problem where a clickable 'kill application' key wouldn't have worked. I was in an full-screened (F11) Firefox window trying to save a picture when everything but the mouse because unresponsive. I had already seen some other application open up a secondary window underneath the originating window before, so I suspected that was what was up again.  In windows I would have instinctively hit Ctrl+Alt+Del, switched tasks, and forced FF to minimize. In Ubuntu however, I had to come up with random combinations of keys and eventually thought to try Alt+F4ing. The switch window screen popped up but strobed like it and FF were fighting for top screen. Somehow I accidentally got the picture save dialog to appear on top, saved the picture, and effectively unfroze everything and continued working.

Annoying and frustrating... Is there any hotkey combination that will allow this type of issue to be solved easier next time?

---

