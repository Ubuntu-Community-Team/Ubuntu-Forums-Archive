---
title: "scale gui"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by error.del.gato on 2007-04-24
*new to ubuntu*

I've set up on a A22m with limited graphics abilities... it maxes out with a 800 x 600 display.

Is there a way to scale the interface so that the menus and titlebars are smaller so it appears as if I have more desktop space and windows are smaller by default?

For example, in OS X, this can be accomplished with:
*******************************************
AppleDisplayScaleFactor

To change the scale for the entire system, type the following in a Terminal window, then press Return:
defaults write NSGlobalDomain AppleDisplayScaleFactor 0.5

log out/in

restore:
defaults write NSGlobalDomain AppleDisplayScaleFactor 1

log out/in

per app:
defaults write com.apple.iTunes AppleDisplayScaleFactor .75

log out/in
*******************************************


Any suggestions appreciated.

---

### Post by metra on 2007-04-24
Have you tried to change the screen resolution?

In the main panel go to   System>Prefrences>Screen Resolution, you can change it to 800x600 there.

Welcome to Ubuntu, is this for a "testing/play" computer, or have you switched your main computer?

---

### Post by johnny4north on 2007-04-24
there no easy way to adjust size of menu icons and panels.   you can right click on icons and menu and do some small adjustments.  i believe the best way is to go here [http://www.gnome-look.org/](http://www.gnome-look.org/) and download smallest themes menu and icons.  im looking right nows will take awhile.  i have the same problem, with laptop.  please post your solution if found. i will post mine here. thanks..:)

---

### Post by error.del.gato on 2007-04-24
> **metra said:**
> Have you tried to change the screen resolution?

In the main panel go to   System>Prefrences>Screen Resolution, you can change it to 800x600 there.

Welcome to Ubuntu, is this for a "testing/play" computer, or have you switched your main computer?

Its a crummy graphics set with an older smaller LCD, it maxes out at 800 x 600, which it displays fine. This is a 800MHz PIII A22m ThinkPad w/ 512MB RAM, 40GB HD, that I'd like to put to good use. 

I guess I'm feeling crowded in 800 x 600 as I haven't used a resolution that small in a long time. All I could think to do was change the default font sizes to 8 pt (smallest allowed) and get properties on the top and bottom bars to adjust them to their smallest size (like 19 pt or something). If there were a way to lower the default fonts point sizes to 6 pt, I'd try it, but I was really hoping the interface was easily scalable.

I don't suppose there's a way to emulate 1024 x 768 on a 800 x 600 LCD? With this very laptop & XP sttb, I used to use VNC to connect fullscreen to an OS X 1024 x 768 desktop, and the vnc client *scaled* the screen (I had to figure out the ration w/ trial & error, it liked ?25:32 or something).

---

