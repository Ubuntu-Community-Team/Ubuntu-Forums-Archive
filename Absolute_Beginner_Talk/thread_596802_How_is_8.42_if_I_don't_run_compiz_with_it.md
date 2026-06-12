---
title: "How is 8.42 if I don't run compiz with it?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-29
Here is the deal.  Right now, I'm using 8.37, the drivers available in the repos.  For whatever reason, I can't run a 3d game without it completely and utterly freezing my computer (I've tried with Open Arena and that penguin racing game).  I can't ctrl-alt-f2 to any terminal and I can't kill the xserver; the only option I have is to reset the computer with the reset button.

I figure it has to be a driver problem.  I don't know how to install drivers manually, so I'm going to use Envy, basically.  I can get 8.40 or 8.42.  I've heard 8.42 'causes video problems and slow scrolling in Firefox, but ONLY if compiz is running.  Is that true?  I don't have compiz now because I'm using fglrx, so I can do without it, but I do want to be able to run 3d games without my machine freezing.  Is 8.42 good enough for that or should I get 8.40 still?

My specs:
Athlon XP 2800+
1 gig ram
Radeon 9500 Pro
Ubuntu 7.10

---

### Post by asmoore82 on 2007-10-29
you're probably best off staying in the repos.
I can't ctrl+alt+f1/f2 without fglrx going 99.9% CPU no matter which version I've tried.
I ran the newest 8.42 for a while last week;
AIGLX/compiz did work but there was an overall regression in OpenGL performance and
some weird pointer glitches and lines in the sreen that won't go away without a reboot and
that ONLY happen with 8.42;
I've now switched back to 100% Repos :KS

---

### Post by TheOrangePeanut on 2007-10-30
Well, like I said, the repo drivers crash every 3d application I've thrown at it.  What about the 8.40 drivers?  Should I give them a shot?

---

### Post by marsmissionaries on 2007-10-30
> **asmoore82 said:**
> you're probably best off staying in the repos.
I can't ctrl+alt+f1/f2 without fglrx going 99.9% CPU no matter which version I've tried.
I ran the newest 8.42 for a while last week;
AIGLX/compiz did work but there was an overall regression in OpenGL performance and
some weird pointer glitches and lines in the sreen that won't go away without a reboot and
that ONLY happen with 8.42;
I've now switched back to 100% Repos :KS

Those glitches normally go away if you turn your  monitor off and back on.

As for 8.42, go for it, but there are still bugs. ATI reccomends 8.40.

---

### Post by voided3 on 2007-10-30
Here's my summary from experience on an x1300pro:

8.37 = stable, decent performance except for some games with settings higher
8.40 = a little quicker, Google Earth didn't work with it when I tried it
8.42 = best performer, but I had glitches on the desktop sometime with water marks that looked like dead LCD pixels and in-game brightness controls would be inoperable

Conclusion: stick with repos until 8.43

---

### Post by 3rdalbum on 2007-10-30
If you're having trouble at specific times (i.e. when logging out, running 3D programs etc) on ATI cards, it does often help to upgrade the driver. ATI's drives regress like hell - you can upgrade to the next version and it fixes the problem, then upgrade to the version after that and the problem reappears. But it's probably a good idea to try it, as long as you are reasonably confident that you can get everything back to the way it was before attempting the ugprade.

---

### Post by TheOrangePeanut on 2007-10-30
Well, whatever I did, I broke it.  I disabled the restricted drivers and used Envy to install 8.42.  Well, that fudged up something awful so I uninstalled the drivers using Envy, then uninstalled Envy itself.  I tried to re-enable the restricted drivers, but x always crashes.  When I do glxinfo I get this:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


Whatever I did, I can't seem to get any drivers working except vesa.  I broke it bad, can anyone help?

---

### Post by TheOrangePeanut on 2007-10-30
Somehow, and I don't know how, I managed to get my drivers at least in a usable state.  I did it through messing with Envy and the restricted drivers manager.  Now I'm back on the repo drivers (8.37) and I have direct rendering, but I still can't run 3d applications without it freezing my computer.

Anyone have any advice, or am I stuck until newer drivers are in the repos (when 8.04 is released I guess)?

---

