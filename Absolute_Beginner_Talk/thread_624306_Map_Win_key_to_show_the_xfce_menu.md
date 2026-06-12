---
title: "Map Win key to show the xfce menu"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by nantax on 2007-11-26
Can somebody help me map the Win key so that it will show up the xfce menu just like when I press ctrl+esc.I would like to mimic the start menu behavior from WinXP.

 I have tried going to the Settings -> Keyboard Settings -> Shortcut Tab -> add new theme (because you cannot edit the default theme) and added the xfce-popup-menu and pressed the Windows key. But after exiting the dialog box, nothing happens when I press the Windows key. Also the shortcut says that its SUPER+SUPER_L. What does that mean? 

Thanks in advance.

---

### Post by LowSky on 2007-11-26
I use Gnome but this should work because I just mapped mine to  Super L (aka windows key)

---

### Post by nantax on 2007-11-26
> **LowSky said:**
> I use Gnome but this should work because I just mapped mine to  Super L (aka windows key)

Okay I tried mapping the key but it does not work. Pressing the windows key does not show the xfce menu, and the shortcut says its SUPER+SUPER_L (I only pressed the windows key without touching any other key) not like your that its only SUPER_L. Is there a way to edit this? I sure can't edit it once it set. (It will only allow me to change the command and not the key press).

---

### Post by nantax on 2007-11-28
Okay, let me just bump this thread and see if somebody can help me map the win key to show the application menu.

I have no real problem since I switched to Xubuntu and installed one at the office on a spare pc. But I want to make some minor things work so it will stop bugging me when I'm using the pc.

1) I really want to make the win key work, can I edit some file to change the value of SUPER+SUPER_L to just SUPER and see if that will work?

2) How do I activate my screensaver? I just clicked on the restricted driver message on the task bar and the animation of the screensaver is now a lot smoother (nvidia fx-550). Problem is I don't get to see them when I'm idling. The screen just turns black. (I think its in sleep mode).

3) During boot up and going to the login screen, the display jumps from one color to another, black during the splash screen, blue when transitioning to the login screen, then brownish (like the theme color of this forum) just before displaying the desktop and then finally black (black desktop with no background picture). Is there a way to make the color uniform? Plain black background from start to desktop would be great.

Other than those listed above, my Xubuntu installation is working perfectly.

P.S.

I also would like to thank the very active member of this forum for the help that they extend to us who are still trying to learn a new OS. I have learned a lot just by reading the answers to the question posted here. *cheers to all*

==Edit==

Also one last question... I had an Ubuntu installation from a long time ago and I made some changes on the boot entry, I forgot what it was and I'm not exactly sure whats the keyword to look for. What it did was there was no loading screen, but screenfull of text will show during boot process and also another command that changes the text screen resolution so that lines will not wrap around. I think booting that way is a lot cooler than the default mouse with progress bar... :)

---

### Post by nwhite on 2008-06-04
The windows key doesn't work by default as it's registered as a 'modifier key' by X, (e.g. like control or alt).

Adding the following to the file .Xmodmap in your home directory will make it work like any other key, after restarting X:

```
remove mod4 = Super_L
```

If you want it to work immediately just type the following into a terminal:

```
xmodmap -e "remove mod4 = Super_L"
```

If you want to map the right windows key to a particular function, do the same thing but with Super_R.

If this doesn't work for you enter "xmodmap" into a terminal and check for any references to Super_L in the modifier list. If you see any, adjust the above code appropriately.

After this the XFCE keyboard bindings should work fine for these keys.

Hope this fixes things for you :-)

---

