---
title: "Interesting beryl problem"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by spum on 2007-08-31
I don't know if this is specifically beryl or not, but it's an interesting problem nonetheless.  I had beryl up and running fine last night.  I was doing something with firefox when firefox stopped responding.  I closed firefox and restarted my computer.  When the computer started up, all of my windows were missing the title bar (the bar with the minimize, maximize, and close buttons).  I opened up the beryl settings manager, and the only option across the top was General Options.  Window Management, Desktop, Visual Effects, Accessibility, Extras, Development, and Image Format were all missing.  I assumed this was a beryl issue so I uninstalled beryl.  That didn't fix the problem so I reinstalled beryl.  The options in the beryl settings manager are back, but I still have the same problem with the missing window borders.  It's pretty annoying because I can't drag any of my windows around on the desktop without that title bar.  All of the other settings in beryl remained intact so I wonder if there was some setting that I unknowingly applied that disables beryl while it's running.  Anyone have any ideas?  Let me know if a screen shot would help.  I should be able to get one up.

---

### Post by soapytheclown on 2007-08-31
Have you installed emerald theme manager (its in synaptic)?
How are you loading beryl anyway? using beryl-manager? - if you are you should be able to right click on the task tray icon and choose window decorator - should be set on emerald.

if youve got emerald installed hit alt-f2 and type in emerald and see if they appear.

if those dont work, you might have to enable some stuff in your /etc/X11/xorg.conf

---

### Post by marx2k on 2007-08-31
One minor addition to the last comment. I always hit alt+f2 and type "emerald --replace" not sure if that makes any difference in the end result.

Also, have you considered Compiz Fusion, since Beryl is about to be a dead fork?

---

### Post by BobCFC on 2007-08-31
yes you might want to try:    emerald --replace


if this works you can add it to your startup programs in System->Preferences->Sessions after you launch Beryl



EDIT: compiz-fusion is built into gutsy gibbon anyway.. only 6weeks or so to wait

---

### Post by spum on 2007-08-31
> **soapytheclown said:**
> Have you installed emerald theme manager (its in synaptic)?
How are you loading beryl anyway? using beryl-manager? - if you are you should be able to right click on the task tray icon and choose window decorator - should be set on emerald.

if youve got emerald installed hit alt-f2 and type in emerald and see if they appear.

if those dont work, you might have to enable some stuff in your /etc/X11/xorg.conf

Emerald theme manager is installed.

I load beryl manager with Applications -> System Tools -> Beryl Settings Manager.  Once that is open, I can't hit the X to close it (which would send it to the task tray).  If I minimize it, it just goes to the panel.  Is there another way to close applications (like alt+f4 or something) that would send it to the taskbar? FYI alt+f4 just closes the program entirely.  In any case, without it being on the task tray, I don't see where else I can go to select the window decorator.

Alt+f2 didn't do anything.

---

### Post by BobCFC on 2007-09-01
> I can't hit the X to close it (which would send it to the task tray). If I minimize it, it just goes to the panel. Is there another way to close applications (like alt+f4 or something) that would send it to the taskbar?

I am not clear what you mean by this you may want to restate the problem.

Do you mean that you are trying to carry on without your title bar lol, I think you should fix it or do without beryl.  You might be able to use alt-space (or right click on taskbar) to get by.  You can also use <windowskey><leftmousebutton> to move a window but you shouldn't have to live like this.


The 'emerald --replace'  command does the same thing as 'select window decorator' from the menu, you can also do metacity --replace or kwin --replace to restore gnome and kde desktops respectively.

It sounds like you typed 'emerald' instead of 'emerald --replace'??  Although it doesn't fix everyones machine.

If you want beryl manager to go straight to the tray without opening the window you can launch it automatically on startup without needing to launch from the menu, goto System->Preferences->Sessions and on startup programs click add, give a name and in command put beryl-manager.   (You can add emerald --replace to startup programs after you lanuch the manager if that works for you.)


As I say only 6 weeks till compiz-fusion is built into ubuntu anyway


EDIT:  if by Alt-f2 did nothing you mean that it didn't even open the run window... then just use the terminal instead Applications->Accesories->Terminal

EDIT2:   I see alot of people on the forums with the same problem and fix it by adding this to the device section at bottom of of xorg.conf

> Option "AddARGBGLXVisuals" "True"

so it will look like


```
Section "Device"
    Identifier     "nVidia something something"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    .....
EndSection 
```

You will have to be root to save this file such as:   gksu gedit /etc/X11/xorg.conf

Then restart X  with   Crtl-Alt-Backspace

---

### Post by spum on 2007-09-02
> **BobCFC said:**
> Do you mean that you are trying to carry on without your title bar lol, I think you should fix it or do without beryl. 

This is exactly what I'm trying to do!  I've tried everything that's been suggested so far, but with no luck.  I tried to put beryl manager in the start-up, but it didn't pop up on start up.  I might just have to reformat and reload ubuntu.  Anyone have anything other ideas?

---

### Post by BobCFC on 2007-09-03
> **spum said:**
> This is exactly what I'm trying to do!  I've tried everything that's been suggested so far, but with no luck.  I tried to put beryl manager in the start-up, but it didn't pop up on start up.  I might just have to reformat and reload ubuntu.  Anyone have anything other ideas?



Did you do the 

Option "AddARGBGLXVisuals" "True"


thing too?  sorry that was a late edit I should have made a new post

---

