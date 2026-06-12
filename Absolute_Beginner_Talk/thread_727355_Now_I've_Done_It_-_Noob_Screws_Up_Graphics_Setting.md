---
title: "Now I've Done It - Noob Screws Up Graphics Settings"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by colinpollock on 2008-03-17
Hey All,

I am a complete noob to Linux, with minimal knowledge of the terminal commands. 

I'm afraid I really screwed up my computer.  I have a HP ZE4325US that I recently installed Gutsy (7.10) on. I have it set up to dual boot to Windows XP, with the default as Ubuntu.  Although it took seemingly forever to boot up, it was working fine once it got going.  That is until I thought I would goof around with the graphics card setting.  I noticed while watching some video that the screen had considerable flicker.  I thought I would change the graphics card to a different driver to see if it would improve the situation.  Now, when I boot up my computer, the graphics are so screwed up, I cannot see what to do to get back to how it was before.  

Here is what I can tell you.

Computer: HP Pavilion Laptop 
Model: ZE4325US
Graphics: ATI Radeon Mobility IGP 320M

I can reboot into recovery mode, and suspect I will have to make the fix by this means.  The problem is that I lack any knowledge of Linux terminal commands.  I was able to send one command:

grep Driver /etc/X11/xorg.conf

The response was:

Driver  "kbd"
Driver  "mouse"
Driver  "synaptics"
Driver  "wacom"
Driver  "wacom"
Driver  "wacom"
Driver  "ati"

I suspect the last line that currently says "ati" pointed to something else before.  Can someone help me figure out what that was, and how I go about getting it back to before?  If need be, can I simply edit the xorg.conf file and reboot my computer?  I've seen in some forums reference to fglrx, radeon and vesa as drivers.  How can I try one of these?

I've searched these forums, but have not encountered any indentical problems, although many have problems with the graphics card I have in my computer.

Any help anyone can provide would be greatly appreciated.

---

### Post by fredbird67 on 2008-03-17
I know of two things you might be able to try.  If you're able to boot into the X server, you might want to try Ctrl-Alt-Backspace.  This will restart the X graphical server.

If that doesn't work, or if that's not possible, from the command line, you should be able to type "sudo dpkg-reconfigure xorg-server" (minus the quotes), enter your password when prompted, and then that should automatically reconfigure your graphics settings.

Good luck and lemme know what happens on this, OK?

Fred in St. Louis

---

### Post by handydan918 on 2008-03-17
If you are in single user mode (rescue) you can do ```
dpkg-reconfigure xserver-xorg
```
That will give you a series of questions to answer about your hardware. If in doubt, it is generally safe to accept the defaults. 

Post back if you get stuck.

---

### Post by colinpollock on 2008-03-17
Stupid question - How do I boot into X-Server?

Next stupid question - I tried "sudo dpkg-reconfigure xorg-server" and the response came back (after many lines of feedback) that says

usr/sbin/dpkg-reconfigure: xorg-server is not installed

What does that mean?

---

### Post by Ripfox on 2008-03-17
At the log in select "sessions" and log into a fail-safe terminal then run the command listed above.

Sorry Edit: try running the command > sudo aptitude install xorg

---

### Post by colinpollock on 2008-03-17
> **handydan918 said:**
> If you are in single user mode (rescue) you can do ```
dpkg-reconfigure xserver-xorg
```
That will give you a series of questions to answer about your hardware. If in doubt, it is generally safe to accept the defaults. 

Post back if you get stuck.

Okay, this seems to have gotten me back to square 1.  Thank you very much for your help thus far.

Now if I may hijack my own post, can you possibly give any insight onto how to improve video playback?  I have considerable flicker, even when video is played in a small window.  I'm using Totem Movie Player V. 2.20.0 using GStreamer 0.10.14 and GNOME.

Should I consider trying to find another graphics driver?  Or can I adjust another setting to improve this?

---

### Post by Ripfox on 2008-03-17
Don't run my command now that you are back to sqare one ok? :)

As far as that goes, what version of Ubuntu are you running? What video card?

---

### Post by colinpollock on 2008-03-17
I'm running Gutsy (7.10) on the following computer:

Computer: HP Pavilion Laptop
Model: ZE4325US
Graphics: ATI Radeon Mobility IGP 320M

---

### Post by handydan918 on 2008-03-17
Try checking synaptic under "restricted drivers". Look for ati and fgrlx.

---

