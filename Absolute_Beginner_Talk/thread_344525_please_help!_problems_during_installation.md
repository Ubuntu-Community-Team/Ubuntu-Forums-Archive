---
title: "please help! problems during installation"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by frogger fodder on 2007-01-23
hi there

I am really new to the whole linux thing, so please bear with me.

When i boot from the edgy desktop cd and select start ubuntu, an error message comes up saying:
*Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"* 

I clicked yes and it brought up some basic info. And then it says: 
"*Would you like to view the detailed X server output as well?*"
This brought up some basic info again.

And then it said 
*"X server is now disabled. Restart GDM when it is configured correctly."*

And after that it just brings up a blank screen. I am using a radeon X600 256mb graphics card, just so you know.  I read somewhere to do the following:
at the boot screen press F6 and replace the typed "splash" with "break=botttom"
then type " chroot /root nano /etc/x11/xorg.conf
then change the driver by replacing "ati" with "radeon". But when i enter the "*chroot /root nano /etc/x11/xorg.conf*" bit, the editor screen thing comes up but there is nothing written in the window, so ofcourse i cant even change anything because nothing is there to change.'

i have absolutely no idea what to do, and changing from windows xp is proving a much harder task then should be expected. i am ripping my hair out due to extreme frustration and i would really appreciate some help.

cheers

---

### Post by CowzRule on 2007-01-23
try ```
chroot /root nano /etc/X11/xorg.conf
```
notice the capitol letter X in X11. Linux is case sensitive.
Also, if replacing "ati" with "radeon" doesn't work, try "vesa"

Just in case you need to know; with nano, the arrow keys moves the cursor, "Ctrl+o" then "Enter" saves the file, "Ctrl+x" exits nano.
Then type "startx" to start the xserver.

Hope that helps

---

