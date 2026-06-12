---
title: "[SOLVED] screen magnifier that _follows_ mouse"
date: 2007-12-01
forum: Assistive Technology &amp; Accessibility
---

### Post by ingo on 2007-12-01
Hi,

I am looking for a magnifier that literally _follows the mouse_ - not a window stuck somewhere at the edge of the screen. Personally I find it not very intuitive to use at all.

Is there such a thing? I opt not to use gnopernicus, orca, kmag or xzoom for the above reason and am desperately looking "for the real thing" :)

Thank you in advance.

---

### Post by RCC2k7 on 2007-12-01
If using Ubuntu 7.10 you have two options:

1. Use Orca. By default Orca follows the mouse. If your video card supports composite mode, Orca can even magnify under itself. If this is the case, you just set the top and left values of the zoom window to zero and the bottom and right edges to the highest setting supported for your screen resolution using the Magnifier tab of the Orca Preferences window. And voila, you have a full-screen magnifier that tracks the mouse and other events.

2. If your video card supports 3D Desktop effects, install CompizConfig Setttings Manager from Synaptic. This will add a Custom button to the Desktop Effects tab you get on the Appearance dialog, found on System menu, Preferences. Make sure Enhanced Desktop Zoom is enabled and in the Settings for the Enhanced Zoom plugin, make sure Sync Mouse, Scale Mouse Pointer and Hide Original Mouse Pointer are all checked. To magnify/unmagnify, hold down the WindowsKey and roll the mouse wheel away or towards you. To toggle color inversion, hold down the WindowsKey and press N. This method only tracks the mouse and program windows, but not the highlight in menus and lists or the typing caret.

---

### Post by ingo on 2007-12-02
Thank you for your quick answer. I tried orca but I could only get it to display the magnification in a zoom window - not a lens that actually follows the mouse...

And I am afraid compiz is beyond the capabilities of my computer :(

---

### Post by RCC2k7 on 2007-12-02
Ah, now I understand. Neither option will give you what you are looking for. The Enhanced Zoom plugin for CompizFusion only does full screen magnification, and Orca's is a stationary window that can be resized, but none is a lens around the mouse pointer.

This said, I don't know if gnome-mag can do that with a command line. Orca's magnification is a front end to gnome-mag but other users here have used gnome-mag on its own with command line arguments.

---

### Post by linbetwin on 2007-12-04
Ingo, you can try this: [http://magnifier.sourceforge.net/#download](http://magnifier.sourceforge.net/#download).

It's a resizable window that follows the mouse pointer. It works on Windows, Linux, BSD and other *NIX systems. Tell us if it works.

---

### Post by ingo on 2007-12-04
linbetwin,

you are THE MAN!!! That tool is quite simply wonderful! I've been through a number of forums and nobody has been able to help me, yet everybody seemed to be crying out for something as intuitive as that!!! I will pass on the info.

In case you are a developer - superb piece of work. This is just like the real thing. Only shame is that I do not appear to be able to type while I am focusing on something :( To add this functionality would be to make this piece of software complete.

FYI, I installed it using the bz2 version. The readme.pdf stated the very easy installation instructions succinctly and I it runs a treat on my debian etch system.

Cheers!!!

---

### Post by charonn0 on 2008-01-17
An excellent program!! I agree with the OP about the ability to type/click, though.

---

### Post by pyromanic123boom on 2008-08-24
I know this is old, but..this is one of the luckiest finds I have found on the forums. I was searching for a hour or two for a program I could use when I made some screen capture videos (for magnifying an address bar, etc). thanks  for finding this

---

### Post by echo47 on 2009-04-29
Ah, this is a wonderful feature.  Reminds me of the magnifier in OS X.  I do have one problem though:
when I split my desktop across my laptop and an external monitor, the magnification only works on the external monitor.  Doing the same command on the laptop screen causes the mouse to go haywire and stick to the left side of the screen but nothing gets magnified.
Only by pressing the commands to zoom out all the way does the mouse become unstuck. 
Anyone have any experience with this?

---

### Post by ingo on 2009-04-29
Well, I now use KDE4's inbuilt screen magnifier. It is _really_ good. Having said that - it is a lie - I used to use it but I got myself a 24" screen, so I'm happy as pie and have no further need for zooming into any part of the screen :)

---

### Post by ingo on 2009-04-30
@ echo47

Yep, I don't think that can be changed. It is good for reading only :( I really recommend KDE4 with its screen magnification system. It is dead easy and not nearly as complicated to set up as compiz (but I think even that is a doddle these days).

---

### Post by Rytron on 2009-12-10
> **linbetwin said:**
> Ingo, you can try this: [http://magnifier.sourceforge.net/#download](http://magnifier.sourceforge.net/#download).

It's a resizable window that follows the mouse pointer. It works on Windows, Linux, BSD and other *NIX systems. Tell us if it works.

How do I use this [http://magnifier.sourceforge.net/#download](http://magnifier.sourceforge.net/#download) program?

Also does anyone know how to get this magnifier in this video?
[http://www.youtube.com/watch?v=7JapQj71Sso](http://www.youtube.com/watch?v=7JapQj71Sso)

---

### Post by skierpage on 2013-04-26
> **linbetwin said:**
> Ingo, you can try this: [http://magnifier.sourceforge.net/#download](http://magnifier.sourceforge.net/#download).

It's a resizable window that follows the mouse pointer. It works on Windows, Linux, BSD and other *NIX systems. Tell us if it works.

It's still out there in 2013, magnifier 3.5 uncompresses and runs OK on Ubuntu 12.04.But it doesn't handle multiple monitors. 

[LIST]
[*]It squishes my main monitor screen before displaying a magnified version. 
[*]It won't magnify what's on the second monitor. 
[/LIST]
It's a lot more lightweight than installing KDE's KMag, which if you don't have any other KDE programs wants to install 154 MB of KDE libraries.

(I ran magnifier from its uncompressed directory and it works though it doesn't show it's nice border unless you run [FONT=courier new]sudo install.sh[/FONT] .)

---

### Post by overdrank on 2013-04-26
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

