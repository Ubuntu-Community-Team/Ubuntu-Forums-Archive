---
title: "no window manager"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by benner on 2007-03-24
i just installed the new beta of feisty and have had a terrible time with it.  i think i will need more than one post to solve them all.  the one that is bugging me the most is concerning the window manager.  when i open a window, there is no minimize, maximize, close option anywhere, i can't drag windows or move them around at all.  when i open anything, it covers the 'applications','places' etc... toolbar.  i can't drag windows out of the way to access the menus and can't minimize them so i can only do one thing at a time.  when i tried the hide visible window button in the lower right, it gives me some warning that i don't have a window manager.  same goes for when i select 'window' to look for some settings to change in the admin menu.  any ideas?

---

### Post by eljalill on 2007-03-24
Does anyone else in the Feisty Forum have that problem?

but try
```
gnome-wm --restart
```

---

### Post by benner on 2007-03-24
brilliant!  worked like a charm.  i hope it stays that way when i restart.  haven't tried yet.   but thanks a lot.

---

### Post by benner on 2007-03-24
when i rebooted, it was messed up again.  i had to 'sudo gnome-wm --restart' again.  how can i fix it permanently?

---

### Post by eljalill on 2007-03-24
You have to make sure it loads at startup...
you could try putting it into .config/autostart ... 
just copy a .desktop there, rename it and change the "exec" line to gnome-wm (--restart) .

Does that work?

---

### Post by ComplexNumber on 2007-03-24
**benner**
i don't know if you're aware of this, but fiesty is still beta software. you will be bound to get a few hiccups along the way.

---

### Post by benner on 2007-03-24
i was aware of that and am trying to use this as a learning experience.  i was probably a bit too eager to install but my edgy install was buggy anyways and i read a ton of posts where people claimed that feisty was already more stable than edgy when it was at the herd 5 stage.  in any case, i appreciate any help that folks are willing to offer.  i currently have 3 problems, 2 of which i have posted.

1, the windows manager (i don't quite understand eljalill's suggestion but that is the next thing i will work on...)

2, my grub is messed up (i have another post here about that, someone asked me to post my grub listing and then, unfortunately must have been called away because i never got an answer

3, (small problem) i can't seem to get my monitor resolution any higher than 1024x768 even though it is a wide screen, 19" lcd

thank you for taking the time to try to help me out...

---

### Post by eljalill on 2007-03-24
Ok, then I'll try to make it more clear:
In ~.config/autostart are programs that are started when logging in.
I run beryl and my beryl manager is in there for example.

Usually the programs in there are there in the form of a .desktop script, or at least that's the case with me. 
So what you could to is open one of those .desktops, save them under a differnt name, and modify them, so that they will tell the computer to open the gnome-wm. You do that through changing the line that start "exec". Just type the command there.

On second though, you could of course also try to do that in the GUI. 
Go to system>preferences>sessions , and see, whether there is any possibility to set the gnome-wm in the startup programs. Or in any of the other sessions options for that matter... :)

Ok now?

---

### Post by benner on 2007-03-24
i couldn't find .config/autostart but i was able to do it the gui way that you suggested.  i will try to reboot now.  thanks.  back in a minute...

---

### Post by benner on 2007-03-24
it didn't work.  but it is still there.  system > preferences > sessions and the command is gnome-wm --restart

when i type it into a terminal it works though.

---

### Post by eljalill on 2007-03-24
hm. 
Does it work better, if you 
either leave out the --restart
or try --replace instead?

More thoughts:
you could try metacity instead of gnome-wm,
also: did you ever could consider enlightenment ;) 
(I won't recomment beryl here... it took me at least quite a lot of setup)

---

### Post by benner on 2007-03-24
tried --replace and got 

Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

just gnome-wm gave me the same thing.  but i guess i need to reboot, and then try it while it is still screwy...  back in a minute.

---

### Post by eljalill on 2007-03-24
Nah, sorry,
I meant not to type it into the terminal, but to have it in startup programs (under system>preferences>sessions).
Sorry if I was unclear.

Or are you getting these error messages at startup?

---

### Post by benner on 2007-03-24
i rebooted, had the problem, typed into the terminal, that fixed it, then i typed what you suggested.  those were the errors i got.  i guess because it had already been run.  i will try to put it into the sessions menu and reboot again now.  thanks for staying with me...

---

### Post by benner on 2007-03-24
didn't work.  how do i try metacity?  feisty has compiz installed (i think) but it was causing all sorts of problems so i had to turn it off.

---

### Post by benner on 2007-03-24
solved.  i went to system > preferences > sessions and just added 'metacity' where the command was 'metacity' and rebooted.  it worked.

---

### Post by eljalill on 2007-03-24
Glad it worked. 
although enlightenment is supposed to be quite cool ;)

---

### Post by jkeyes0 on 2007-03-24
I had this same sort of problem on my  laptop with Beryl installed. I opened the Beryl Manager and told it the default window manager was Metacity, and it fixed the problem.

---

