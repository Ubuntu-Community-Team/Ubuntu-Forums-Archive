---
title: "Problem with desktop"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Baio on 2007-08-19
hi all. I know, i'm totally noob here. Anyway. From this evening I've got a problem with my desktop: it's totally black (so no background image, no folders, stuff like that), there are no icons, i can't do *anything* with it (stuff like right-button mouse click, new folders... and so on). I'm sorry but I can't describe the problem in a better way than that. I've upgraded today Compiz, could this be the problem?

p.s. sorry if my english is terrible, but you know, I'm italian after all XD

waitin' for answers, and sorry if the answer is already known. ^^

---

### Post by Lithium17 on 2007-08-19
Is compiz the same as beryl? I know the two have joined but is there two different softwares?  If so I have had no problem at all with beryl-manager on Ubuntu 7.04.  only thing I can suggest is can your graphics card cope with the load, maybe you should turn off some effects.

---

### Post by omegamike3 on 2007-08-19
I would try booting into recovery mode or off of the live cd, once there you may be able to either fix Compiz or remove it, depending on what's gone wrong. sometimes, if it is something simple, just restarting the X server may help. when you're at the blank desktop, try ctrl+alt+backspace, worth a shot, sometimes the simplest answer...

---

### Post by Baio on 2007-08-20
ok, I did it. thanks to all.

p.s. Anyway I tried ctrl+alt+backspace, but it didn't work

---

### Post by jordanmthomas on 2007-08-20
Try running nautilus by pressing Alt + F2 and typing
```
nautilus
```

That may bring your desktop back.

If not, be sure you haven't set your cube's transparency to 0 or something silly like that.

---

### Post by misfitpierce on 2007-08-20
and yes compiz and beryl are 2 diff softwares.

---

### Post by aitorcalero on 2007-08-20
through the console (you can access to it by CTRL+ALT+F1) try to remove compiz and restart

```

aptitude search compiz

```

Remove all compiz stuff

```

aptitude remove "compiz_related_stuff"

```

You can allways install it later, but I recommed use compiz through "Desktop effects" option, in System / Preferences menu.

---

### Post by jppaynesr on 2007-10-06
I have the same problem, I have a menu bar but my desktop icons have vanished, and right clicking the desktop does nothing. Unlike others, I do NOT run compiz.
Here is what I have done recently
1. Installed a synaptic security upgrade 2 days ago, I think it had about 19 files, some were open office, another was skype.
2. Modified some skype preferences
3. I messed around with the Assistive technology preferences, played around with the screen reader, and then turned it off.

Now my desktop is broken, and the menu bar is the wrong color.
My desktop files are still in the folder called /home/me/Desktop

Any ideas?

---

### Post by jppaynesr on 2007-10-06
I just fixed my issue. I ran 'nautilus' from a command prompt and now my desktop is normal again.

Previous to that I had noticed, after a reboot, that the panel that pops up as the system is loading said "the panel", now it says "Nautilus".

Now the only problem is the interactive spell checker is not working.

---

