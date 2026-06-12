---
title: "Question about multiple GUIs"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Goober on 2005-10-10
Ok, I have discovered something about Ubuntu.  Apparently, through Synaptic, I can get KDE, and XFCE.  I want to try KDE, see how it works, but, if I download it through Synaptic, how can I use it, since I am using Gnome now.  You can't have multiple GUIs running at the same time, right?

Also, does having multiple GUIs have anything to do with that little "Workplace Switcher" on the bottom right-hand corner of my Gnome screen, beside trash?  With the 4 boxes, and me being active only in the first?

---

### Post by aysiu on 2005-10-10
[QUOTE=Goober]Ok, I have discovered something about Ubuntu.  Apparently, through Synaptic, I can get KDE, and XFCE.  I want to try KDE, see how it works, but, if I download it through Synaptic, how can I use it, since I am using Gnome now.  You can't have multiple GUIs running at the same time, right?[/quote] Maybe you can. Very little in Linux is impossible. I just don't know how to do it. The usual way to use multiple GUIs is to log out, select the "session" you want (KDE, XFCE), and log back in.

> 
Also, does having multiple GUIs have anything to do with that little "Workplace Switcher" on the bottom right-hand corner of my Gnome screen, beside trash?  With the 4 boxes, and me being active only in the first? Again, I don't know. Usually the workplace is just for different desktops, not different desktop environments, but with Linux--who knows? The possibilities seem endless sometimes.

---

### Post by Goober on 2005-10-10
Hrm . . . well, I'm currently downloading KDE through Synpatic, it asked me to put in the 5.10 CD, and its got 395 files to download, so I'll see what happens in a few minutes, I guess . . .

I guess the best way with Linux is trial and error . . . more of the latter, less of the former . . . ;)

---

### Post by Wolki on 2005-10-10
[QUOTE=Goober]Ok, I have discovered something about Ubuntu.  Apparently, through Synaptic, I can get KDE, and XFCE.  I want to try KDE, see how it works, but, if I download it through Synaptic, how can I use it, since I am using Gnome now.  You can't have multiple GUIs running at the same time, right?[/quote]

You can choose which one you want to use on the login screen.  There is an option called "session", choose Gnome, KDE or whatever you have installed there. If a certain DE/Window manager doesn't create an entry in that menu, ask again for specifics (KDE and XFCE should work fine without additional work)

If you don't want to log out your main session and have a quick look at a certain de/wm, use "New login" in the system tools menu.

> Also, does having multiple GUIs have anything to do with that little "Workplace Switcher" on the bottom right-hand corner of my Gnome screen, beside trash?  With the 4 boxes, and me being active only in the first?

Nope, absolutely not. Those are so called virtual desktops, and you can be active in all of them just by clicking on the boxes. You can move windows there, it keeps each virtual desktop a little more organized. Try it out, many people love it.

---

### Post by codejunkie on 2005-10-10
you somewhat can run multiple desktop enviorments at the same time in linux with xnest but sometimes xnest will lockup when the other desktop enviorment trys to access the hardware at the same time as xnest at least that's what happened to me.
edit: since i mentioned it i figured i'd test it out with breezy i just ran a xfce session through xnest and it ran smooth really nice everything seems to be working 100% compared to when i tried it with warty.

---

### Post by Goober on 2005-10-10
Erm, ok, I installed "kde" via Synaptic, and, well, it seems to have installed all, and I mean all, of the KDE programs, like Konquerer etc, in Gnome . . . 

I'm going to restart, and see if I can access KDE through the login.

---

### Post by Wolki on 2005-10-10
[QUOTE=Goober]Erm, ok, I installed "kde" via Synaptic, and, well, it seems to have installed all, and I mean all, of the KDE programs, like Konquerer etc, in Gnome . . . 

I'm going to restart, and see if I can access KDE through the login.[/QUOTE]

Yeah, it does that. Seems stupid, but makes sense. If I install K3B in Gnome, I want in in the menu, right? Same could apply to all KDE apps. Smeg and Gnome's own menu editors can take care of those you don't actually want.

You don't need to restart, just log out, or hit crtl-alt-del after saving all open files.

---

### Post by Goober on 2005-10-10
I am typing this through KDE, so KDE obviously was installed, however, what happened, I guess, is that a whole whackload of KDE programs got installed in Gnome, and KDE got installed.  So, well, I have questions about KDE, which is substantially different then KDE. Is this the place to ask them, or is there a separate KDE forum?

BTW, I am extremely impressed that Firefox automatically got my bookmarks from Gnome, and that my Gnome folder automatically came over . . . is tghat supposed to happen?

---

### Post by Goober on 2005-10-10
[QUOTE=Wolki]Yeah, it does that. Seems stupid, but makes sense. If I install K3B in Gnome, I want in in the menu, right? Same could apply to all KDE apps. Smeg and Gnome's own menu editors can take care of those you don't actually want.

You don't need to restart, just log out, or hit crtl-alt-del after saving all open files.[/QUOTE]

Sweet Jesus, you're right!  Wow, this is so cool, I can switch between KDE and Gnome in seconds . . . *is in awe*

Linux just gets better and better every day . . .

---

### Post by Wolki on 2005-10-10
[QUOTE=Goober]I am typing this through KDE, so KDE obviously was installed, however, what happened, I guess, is that a whole whackload of KDE programs got installed in Gnome, and KDE got installed.  So, well, I have questions about KDE, which is substantially different then KDE. Is this the place to ask them, or is there a separate KDE forum?

BTW, I am extremely impressed that Firefox automatically got my bookmarks from Gnome, and that my Gnome folder automatically came over . . . is tghat supposed to happen?[/QUOTE]

Of course. It's still the same user, and the same firefox and everything. Just a different desktop environment. Switching desktop environments is nothing like switching operating systems or such. And programs from one usually work without  problems in the other, that's why they're added to your gnome menu.
Ask your questions here, the desktop questions subforum, or the kubuntu subforum, whereever you want.

---

### Post by benplaut on 2005-10-10
it's still the same user, so all files and settings (in theory anyway- and it usually works) will be the same, if you are using the same program as in Gnome. 

Xnest works (btw, the command line for it is "gdmflexiserver --xnest"), btu is not ideal because it only runs at 1024x768, and i haven't figured out how to change it.

have fun!

---

### Post by Goober on 2005-10-11
Erm, what exactly is Xnest?

---

### Post by Wolki on 2005-10-11
[QUOTE=Goober]Erm, what exactly is Xnest?[/QUOTE]

A Picture is worth a thousand words.

---

### Post by Goober on 2005-10-11
Am I correct in thinking it is where you run a GUI (X) within a GUI?

(Unfortunately, I learn best by verbal explanations)

---

### Post by Wolki on 2005-10-11
[QUOTE=Goober]Am I correct in thinking it is where you run a GUI (X) within a GUI?

(Unfortunately, I learn best by verbal explanations)[/QUOTE]

Exactly.

---

