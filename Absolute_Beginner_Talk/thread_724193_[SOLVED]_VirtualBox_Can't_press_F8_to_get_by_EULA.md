---
title: "[SOLVED] VirtualBox: Can't press F8 to get by EULA"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-03-14
I can not seem to figure out how to get VB to capture my mouse/keyboard so that I can get past the XP's EULA (by pressing F8 ). Oddly enter (first part of setup) and escape (to exit) do work.

I installed VB (non-ose) following the steps outlined in the first post here ([http://ubuntuforums.org/showthread.php?t=690713](http://ubuntuforums.org/showthread.php?t=690713)). When I click inside the VB window, I get a popup telling me that my mouse is being captured but am still free to move my mouse around outside my host os (Gibbon).

In addition I have:
```

Reinstalled and tried on a fresh system

Turned off advanced desktop effects (I run compiz)

sudo /etc/init.d/mountdevsubfs.sh start

VB>Settings>USB>Enable USB Controller & Enable USB EHCI Controller (and tried each independently)>Add mouse and keyboard

Ensured VB>File>Preferences>Input>Auto Capture Keyboard is selected

Tried CTRL (left and right)>F8, CTRL ALT F8, etc
```


Any help would be most appreciated, I am getting pretty frustrated!

---

### Post by redwaldmcmanus on 2008-03-14
normall, the right CTRL button controls the keyboard and mouse capture in VB

---

### Post by DamonChyld on 2008-03-14
Yeah, I know that's how to toggle the capture. My problem is that when I click in the VB window I get a popup telling me that mouse is being captured, but am still free to move around Gibbin. If I click again I get the same message repeatedly (after saying ok to the popup). The arrow by the right>ctrl logo on the bottom R changes to yellow and I can press R-CTRL and it will toggle back to black but it does not affect anything one way or the other. 

Also, playing around some more and if I have VB>Settings>USB>Enable USB Controller enabled with my mouse and keyboard added, my mouse will freeze after the Innotec splash screen.

---

### Post by Jose Catre-Vandis on 2008-03-16
CTRL+F8 should do it?

if not, try turning off Compiz, then it should work

another solution was to ```
click the F-LOCK key, the F8 key worked, but then sent the host OS into Standby...

Once logged back into the Host, the install looks to be progressing nicely
```

---

### Post by n0veme6er on 2008-03-17
try shift-F8 

It works for me.

---

### Post by DamonChyld on 2008-03-18
Thanks yall -

I was able to get it working by downloading and installing the binary tar rather than using apt-get.

---

