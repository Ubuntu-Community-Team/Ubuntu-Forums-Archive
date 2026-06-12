---
title: "100 seconds of nothing"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by rangefido on 2007-12-21
hello everybody
I'm brand new to all this and I've just installed wubi - ubuntu which looks and feels gorgeous.
Just one question - what is supposed to happen at bootup? After choosing Ubuntu rather than Windows I get a few lines of text about booting and file systems (should I be seeing that?) and then nothing for 100 seconds. I know it's nothing rather than a black screen because my dead pixel shows.
Then a quick messy page of multicolour splodgy interference before the logon screen appears. 
Is that what should happen?
Thanks all
Mike in the UK

---

### Post by 3rdalbum on 2007-12-21
When you choose Ubuntu, generally you get an Ubuntu logo and then a progress bar, until the X server starts. (the bit where you quickly get the multicolour interference thing and then the login screen). In this case, it seems that either your monitor or graphics card doesn't support the "framebuffer" that is used to draw the progress bar.

If your installed system works, then it's nothing to worry about. If Ubuntu has to tell you something important during bootup, it switches away from the framebuffer and to a basic text screen, which by your description you would have no trouble seeing.

---

### Post by insane_alien on 2007-12-21
sounds like something is borked with usplash. 

once you get logged in(you can log in can't you?) go to synaptic and find the bit that says 'Fix Broken Packages' run that and it should fix it.

also, try and find the drivers for your video card if ubuntu doesn't do it for you.

---

### Post by khughitt on 2007-12-21
Also, to see what is going on behind the scenes, what you can do is when the GRUB menu pops up, highlight Ubuntu and hit "e" to *edit *the boot string. Next remove the "quiet" and "splash" sections, and add a "--verbose" at the end of the line. Hit enter, and then "b" to boot. (The changes are temporary and will only happen for the current boot, so don't worry about messing anything up too much).

Goodluck!

---

### Post by JillSwift on 2007-12-21
I suspect you'll find this thread useful:

[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

Seems there's a little problem with setting an appropriate resolution for usplash on some systems.

---

### Post by rangefido on 2007-12-21
Thanks very much to everybody.
I've spent an hour or two  trying everything on this thread and pretty much everything on the other thread (the 'werd solution' thread) but it's still happening just the same, so I think I'll call it a day and get on with Christmas. Maybe try again when I've more time.
Thanks again everyone for taking so much trouble
Mike in the UK

---

