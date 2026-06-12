---
title: "Terminal Not appearing"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by iharrold on 2007-11-16
I'm using Gutsy 7.10.

Applications->Accessories->Terminal

It starts up in the task bar at the bottom of the screen.  The mouse icon changes to the processing wait icon.  Then nothing.  The Terminal unloads (appears too) from the task bar and mouse icon returns to normal.  

Any ideas?

---

### Post by approaching on 2007-11-16
are you doing anything strange as far as windowing goes? (compiz, awn, etc) does it do this even after restarting x?(ctrl+alt+backspace)

---

### Post by iharrold on 2007-11-16
I rebooted, and I am still having the same problem.  First thing after the reboot, I tried to bring up the terminal window ... and nothing.  About the only thing I can think of is that I switched over to a dual monitor NV driver.  But that makes no sense on why I cannot get the Termianl Window up.

---

### Post by iharrold on 2007-11-19
I am still having this issue.  I checked the "System Monitor" and when I start up the Terminal It appears in the Monitor as the "Gnome-Terminal".  And then it goes away..

Any ideas?  Anyone else having this issue?  I have ran "Update Manager" to get the latest version.

EDIT:  I messed around with the screen resolution and disabled my Dual Display using the Nvidia Drivers on a NV Quadra 4 550 XGL.  Here is what I found.

1900x1400 Dual Display causes the Terminal Window to not load, Firefox and other applications load just fine.
1900x1400 Single Display causes the Terminal window to load, however the window box is all white with nothing rendered on it.  Also, when loading up FireFox, it came up black.
I could not change the resolution to anything other than 1900x1400 without having to "pan" around the screen due to the Ubuntu being larger than the display size.
Removed NV Drivers and using generic drivers, Resolution set to 1600x1200 single display, Terminal Window and Firefox loads just fine.

So it appears to me to be an issue with the NV drivers.

---

