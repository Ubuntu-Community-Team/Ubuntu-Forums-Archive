---
title: "ATI Radeon Graphics card not working with driver"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by duchednier on 2007-04-14
or... something like that
i'm currently going through this tutorial to get beryl
[http://ubuntuforums.org/showthread.php?t=341149](http://ubuntuforums.org/showthread.php?t=341149)
and at step 5, it still says "direct rendering = no" 
in the terminal it says 
duchednier@duchednier-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
duchednier@duchednier-desktop:~$ 

i have installed the drivers twice and done what was needed in this tutorial twice and it still doesnt work, does anyone have any idea how to fix it?

---

### Post by igknighted on 2007-04-14
> **duchednier said:**
> or... something like that
i'm currently going through this tutorial to get beryl
[http://ubuntuforums.org/showthread.php?t=341149](http://ubuntuforums.org/showthread.php?t=341149)
and at step 5, it still says "direct rendering = no" 
in the terminal it says 
duchednier@duchednier-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
duchednier@duchednier-desktop:~$ 

i have installed the drivers twice and done what was needed in this tutorial twice and it still doesnt work, does anyone have any idea how to fix it?

Installing twice may be your problem.  If you can, try to uninstall everything that you have installed related to the ATI drivers.  Then go to synaptic and install the package "xorg-drivers-fglrx".  After this, run the command "sudo ati-config --initial" in a terminal.  No promises, as you have one of the worst vid cards you can have with linux, but this is your safest and easiest bet to get the drivers installed.  By installing multiple times, you may have overwritten some important X.org files, so you might want to uninstall/reinstall X.org.  If it comes to that, you might rather just do a Ubuntu reinstall, it would take a similar amount of time/effort if you haven't done much system configuring yet.

---

### Post by duchednier on 2007-04-14
Ok i tried uninstalling it, in add remove programs the only ati or radeon program is "ATI binary X.Org driver"
my graphics card is in the list of supported cards below, but it wont let me unintstall it, when i click on it it says
ATI binary X.Org driver cannot be nistalled on your computer type (i386)
either the application requires special hardware features or the vendor decides to not support your computer type

but it IS installed because the box is checked, how do i uninstall it?

---

