---
title: "Gutsy questions"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-10-21
Hello all,

I just successfully (or, at least, it seems that way so far) installed Gutsy after having used Feisty for awhile. I have a few weird things to ask about:

1) The title bars in every open window (where the min/max/close buttons live) are enormous! This is quite annoying. How do I get the bar back to normal?

2) Is it normal that my xorg.conf file is blank?

3) How do I make "Touchpad" display in my System menu? When I move the cursor with my touchpad, it feels like I'm dragging the cursor through mud. Also, my vertical scroll is too fast-moving and choppy for my tastes. I'd like to change this, but I don't know how.

Otherwise, everything seems fine! Any help with the above would be fantastic.

---

### Post by earobinson on 2007-10-21
> 1) The title bars in every open window (where the min/max/close buttons live) are enormous! This is quite annoying. How do I get the bar back to normal?
do you have a screenshot? is everything biggger?

> 2) Is it normal that my xorg.conf file is blank?no mine has stuff

> 3) How do I make "Touchpad" display in my System menu? When I move the cursor with my touchpad, it feels like I'm dragging the cursor through mud. Also, my vertical scroll is too fast-moving and choppy for my tastes. I'd like to change this, but I don't know how.
System->Preferences->Mouse?

---

### Post by doctorbighands on 2007-10-21
I just took a screenshot. I attached it below.

Nothing else is out of the ordinary - just the title bars!

I adjusted System>Preferences>Mouse as much as I could. It still feels like I'm dragging the cursor through water. The vertical scroll issue was partially helped by enabling smooth scrolling in Firefox. I may just have to live with a new feel to my mouse.

As for the xorg.conf file: What should I do? Nothing seems to be dysfunctional, but when I type in "sudo gedit /etc/x11/xorg.conf", I get a blank gedit file.

---

### Post by kvonb on 2007-10-21
hahaha, freaky!

Try changing the window decorations from the theme tool, it looks like you have *desktop effects* working so it might be that.

---

### Post by TeaSwigger on 2007-10-21
> **doctorbighands said:**
> I just took a screenshot. I attached it below.

Nothing else is out of the ordinary - just the title bars!

I adjusted System>Preferences>Mouse as much as I could. It still feels like I'm dragging the cursor through water. The vertical scroll issue was partially helped by enabling smooth scrolling in Firefox. I may just have to live with a new feel to my mouse.

As for the xorg.conf file: What should I do? Nothing seems to be dysfunctional, but when I type in "sudo gedit /etc/x11/xorg.conf", I get a blank gedit file.

Hello again, glad to hear you had things going in Fiesty. 

It's /etc/X11/xorg.conf - linux paths are case sensitive and you need to upper - case the X.

You're on the right path though. The xorg.conf settings could impact / account for your naughty mouse's behavior. So try and see what's going on in there. Post it here if you have questions. :)

edit: wow that there's the biggest honkin' title bars ever! yike. Well I don't use gnome much so I'm not the best person to guess, but I'd try changing the theme, especially the window settings, and see if it won't just reset itself and over write whatever was goofed. Failing that, if you haven't already done so, restart X (ctrl + alt + backspace), failing that reboot if you haven't already, and failing that, start hunting for any settings that might influence the title bar in any way - changed any font size settings or anything? Again, not familiar enough with gnome. Luck :)

---

### Post by doctorbighands on 2007-10-21
...theme tool?

Thank you (and hello to you!), teaswigger. The uppercase thing popped my xorg file right open! Now, to sift through and see what might be funky in there...

Here are the relevant contents of xorg.conf. I'm certain someone knows what to fix better than I do.

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


```

---

### Post by crimesaucer on 2007-10-21
> **doctorbighands said:**
> ...theme tool?

Thank you (and hello to you!), teaswigger. The uppercase thing popped my xorg file right open! Now, to sift through and see what might be funky in there...

Here are the relevant contents of xorg.conf. I'm certain someone knows what to fix better than I do.

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


```

What's your Section "ServerLayout" say?

---

### Post by doctorbighands on 2007-10-21
Check this out! I got my super-sized title bar figured out, sorta by accident. Here's what I did:

I went into the desktop effects changer. I downgraded to "None," which immediately shrunk my title bars down to normal (yay!). Then, just out of curiosity and to be ornery, I kicked it back up to "Extra" (the highest setting), and wouldn't you know it: my title bars are still normal! I don't know what happened, but my desktop effects are still intact, and everything is back to normal. Pretty funny!

---

### Post by doctorbighands on 2007-10-21
> **crimesaucer said:**
> What's your Section "ServerLayout" say?

It saaaaaaays...

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

I happen to know that mine is an ALPS touchpad, in case that makes any difference.

(excitedly anticipating helpful reply)

---

### Post by pashashome on 2007-10-21
I had the same problem. Check out this link: [http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login]("http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login")

drvista's post #4 was the key for me. You didn't say if the font was huge when you tried to login or not...it was in my case along with what you mentioned.

---

### Post by crimesaucer on 2007-10-21
> **doctorbighands said:**
> It saaaaaaays...

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

I happen to know that mine is an ALPS touchpad, in case that makes any difference.

(excitedly anticipating helpful reply)

Well, it looks normal to me. Your xorg.conf is correct. Sorry I can't help.

---

### Post by doctorbighands on 2007-10-21
I'll just get used to the mouse issue. It isn't that bad. If that's the worst problem I end up with, I'm pretty sure I'm doing just fine.

There is one other thing: When I go to install new programs (I was going to bring a music player on board), I get the same message inside the Add/Remove Applications window where the description of the program should be:

"Canonical Ltd. provides technical support and security updates for [program]
[program] cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

...where [program] is whatever program I'm trying to view the description of, naturally.

Any idea what this means and/or why every program displays in this manner? I'm going to try to install Amarok in spite of this weird message and see what happens.


**EDIT:  I just attempted to install both Amarok and Kaffeine, and both times, I got the same popup message: "The list of applications is not availabe.[sic] Click on 'Reload' to load it. To reload the list you need a working internet connection."

What gives???

---

