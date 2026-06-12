---
title: "Problem with wine"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by tygr88 on 2007-10-18
I installed wine and then using that i installed CS 1.6..............initially it loaded fine but had no text i resolved that.........after that using winecfg i changed some thing  now the game starts but there is no display.........there is sound and every thing ...........all i can see is the cursor and black back ground

---

### Post by livingtarget on 2007-10-18
Try configuring wine to run in a window it may help you to diagnose your problem. Press alt+f2 and type "winecfg" without the quotes. Then click on Graphics "Emulate a Virtual Desktop", assign it a resolution a bit bigger like 1024x768 and press ok. Now launch CS1.6 and see if it's any better.

---

### Post by cogadh on 2007-10-18
Launch the game from the terminal so that any error messages Wine produces are output to the terminal window. Post those error messages here, it could help diagnose the problem.

---

### Post by Old *ix Geek on 2007-10-18
Keep tweaking its settings in winecfg.  Make one change at a time to see what the results are when you start the game.  If you're using wine for multiple applications, make sure you add this one on the 'applications' tab, so you're only changing settings for this game.

I've had to walk through almost every option in winecfg trying to get certain apps to work, or to work well, but it was worth the time it took.

---

### Post by tygr88 on 2007-10-18
i tried what livingtarget told me to..... the game opens but in a small window and i cannot put it in full screen.....i typed in a resolution of 1440x900

---

### Post by Frak on 2007-10-18
> **tygr88 said:**
> i tried what livingtarget told me to..... the game opens but in a small window and i cannot put it in full screen.....i typed in a resolution of 1440x900
Press Alt+Enter to go to fullscreen.

---

### Post by tygr88 on 2007-10-18
also how do i get out of some application that has crashed......like alt+F4 or Ctrl+alt+del....etc

---

### Post by Frak on 2007-10-18
> **tygr88 said:**
> also how do i get out of some application that has crashed......like alt+F4 or Ctrl+alt+del....etc
alt+f4, but if it gets really messy, Ctrl+Alt+Backspace

---

### Post by aktiwers on 2007-10-18
You need to install the Windows fonts.

```
wget http://www.cynapses.org/tmp/tahoma.ttf
```

And put it in your .wine folder:
```
cp -R tahoma.ttf /path/to/wine/windows/
```

---

### Post by compiledkernel on 2007-10-18
For troubleshooting wine -- [http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

