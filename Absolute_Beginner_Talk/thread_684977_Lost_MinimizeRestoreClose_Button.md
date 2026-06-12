---
title: "Lost Minimize/Restore/Close Button"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by jcparker500 on 2008-02-01
My minimize/maximize/close buttons have disappeared from all of my title bars.  Does anyone know how to get them back?  Also, my keyboard no longer functions properly.  I can no longer hold down a key - I have to tap it.  For instance, normally if I wanted to backspace ten characters back I would just hold down the backspace key until I went back 10 characters.  Now, if I hold it down it only goes back one space.  I would have to tap it 10 times to go back 10 spaces.   If I wanted to make a line of Xs, instead of just holding down the X key, I would have to tap it repeatedly.

This all happened after I tried to turn on desktop effects.  I got an error that said it was unable to start desktop effects.  It was after that that this all started.  So desktop effects are not on.  Any help please?   I really don't want to have to do a reinstall!

---

### Post by Crumpets and Jam on 2008-02-01
> **jcparker500 said:**
> My minimize/maximize/close buttons have disappeared from all of my title bars.  Does anyone know how to get them back?  Also, my keyboard no longer functions properly.  I can no longer hold down a key - I have to tap it.  For instance, normally if I wanted to backspace ten characters back I would just hold down the backspace key until I went back 10 characters.  Now, if I hold it down it only goes back one space.  I would have to tap it 10 times to go back 10 spaces.   If I wanted to make a line of Xs, instead of just holding down the X key, I would have to tap it repeatedly.

This all happened after I tried to turn on desktop effects.  I got an error that said it was unable to start desktop effects.  It was after that that this all started.  So desktop effects are not on.  Any help please?   I really don't want to have to do a reinstall!

Try a restart.

If that does not work press Alt + F2 and type.

```
compiz --replace 
```

---

### Post by jcparker500 on 2008-02-01
Restarting was the first thing I tried.  Nothing happens when I press ALT + F2.  :(

---

### Post by jcparker500 on 2008-02-01
I tried running your command in a terminal window.  It did not work.  Here are the results:
> :~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c57 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048 ): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


---

### Post by jcparker500 on 2008-02-02
Oh well, I just installed KDE  to fix it.  I think I preferred GNOME, but  I didn't feel like reinstalling Ubuntu from scratch again - I just spent two days configuring and updating.  Hopefully KDE 4.0 will be available through the package manager soon (only has 3.5 right now from what I could find).

---

### Post by jcwmoore on 2008-02-02
I have had this happen before, but after a restart it was fine again.  I also think that just restarting gnome solved it for me.  the easy was to restart gnome is by pressing CRTL + ALT + backspace,  make sure you save everything is that key sequence will close your programs, log you out and bring you back to the login in screen.

---

### Post by Zurd on 2008-02-02
Both of your problems happened to me a short while ago and are still popping out from time to time. No need to restart your computer to fix it though, for the minimize button just go into System / Preferences / Appearance / Visual Effects, choose None, then choose back what you just had  before and it'll come back. 

But, if the minimize button disappeared right after you choose to use Desktop Effects, then your computer doesn't seem to be able to display them, you shouldn't use it in this case.

Then for the keyboard problem, System / Preferences / Keyboard, just click and unclick the first check box or modify the horizontal bar of delay or speed to switch it back on.

---

### Post by jcparker500 on 2008-02-02
Hey, thanks - that fixed the keyboard problem!  Unfortunately, no good on the loss of my close/minimize buttons.    You see, Desktop Effects are not on, so I can't go in and turn them off to fix it.

---

### Post by jcparker500 on 2008-02-02
I guess this one must really be a stumper for people!  :confused:

---

### Post by motorbelly on 2008-02-11
I had done some appearance changes and messed things up and I too lost the max/min/close buttons.

After reading this thread I tried System, Preferences, Appearance, Visual Effects and turned it on then off and it brought everything back.

Go figure...  :)

---

### Post by oedha on 2008-02-12
mmm...maybe this will sound silly.....
did you turn off windows decorator ? turn it on
or....when i lost mine....i just rotate the cube :==> ctrl+alt+mouse drag
and i didnt use opacify too

---

### Post by jcparker500 on 2008-02-14
I'm glad the thread was able to help someone, motorbelly.  Since my visual effects aren't on, I can't turn them off to fix it though!  :(

I've gotten used to KDE anyway and am rather enjoying it...

---

### Post by CrazyIndians on 2008-04-17
that was really simple just turn it off and turn it on thanks buddy

---

