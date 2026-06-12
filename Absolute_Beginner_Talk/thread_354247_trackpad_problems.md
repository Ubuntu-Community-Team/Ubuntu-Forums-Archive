---
title: "trackpad problems"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-02-05
I posted about the mic and trackpad problems too close to the same time. The mic  bug is fixed. I got confused about what to do with the trackpad. There were too many differing instructions, and it was too confusing communicating here, and also on launchpad,  So... I let the trackpad problem go. But, it's still a problem that would be nice to remedy. 

Sometimes I have to click many many times to highlight or activate a link or button. And while typing, the cursor will either move to another location, or began flying around on its own. I've been extra careful to make sure I'm not touching the trackpad with my hand while typing.

It's a Dell Inspiron 1300 with i386 and Synaptics touchpad. PLEASE don't ask me to do the same instructions from one of the previous posts. I did not understand what to do then, and still don't understand what to do. And I don't remember what changes I've typed into the Kernel.

But the trackpad is still a problem. If you can help, I'll appreciate it.

---

### Post by RichPicker on 2007-02-08
Bump.

PS: I think the lauchpad,net folks are ignoring me, Ha ha. Ain't ubuntu just grand. It's coming up on a month for me, and this machine is still not right. 

This trackpad is really a pain.

---

### Post by RichPicker on 2007-03-01
Getting closer, I installed GSynaptics and got these resutlts. Is anyone willing to explain how I can make these changes in xorg.conf?

---

### Post by RichPicker on 2007-03-01
I searched and found some files named "xorg.cong" but nowhere in any of those files is there "SHMConfig" that I could set to "True" . And there is no file named "XG86Config" and no line of text with that name in any of the "xorg.conf" files. Any advice?

I've been struggling with this trackpad since the first hours after installing Ubuntu. (since January). I think I'm glad I've found the GSynaptics goody for the trackpad, but am quite puzzled why no Launchpad.net folks or anyone else mentioned it. 

If I could just find the light switch, maybe I'd be able to see, and stop bumping into the furniture.

---

### Post by ubu fubar on 2007-03-01
Hmm, you seem to be talking to yourself here. Mind if I join in?

The SHMconfig line in xorg.conf enables on-the-fly changes to the drivers configuration through external programs such as GSynaptics.

You need to open xorg.conf in an editor and find the section "InputDevice" that's relevant to the synaptics driver. There you can add the line:

```

	Option		"SHMConfig"	"true"

```

Open it by hitting alt+F2 and typing

```

gksudo gedit /etc/X11/xorg.conf

```

and supplying your password. My xorg.conf looks like this (for the touchpad):

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SHMConfig"		"true"
	Option		"SendCoreEvents"	"true"
	Option		"Device"			"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

Remember to add "gsynaptics-init" to your startup programs in Preferences -> Sessions, else your touchpad settings will get reset every time you log in.

Let us know if this helps...

---

### Post by RichPicker on 2007-03-01
Yee Haw. That makes a big difference., Thank you very much.,

For the record: The 'Scrolling" is backwards. When I check the box, scrolling is DISabled. When I UNcheck the box, scroll IS enabled. 

But otherwise, the trackpad works much better. Time will tell if the cursor continues to fly to another location while typing. If it does, I'll bring it to the group's attention.

I'm almost confident enough to try installing Google Earth,. :) 

Thank you much.
R-

---

### Post by RichPicker on 2007-03-02
I still have to tap twice most of the time. I don't think it's a touchpad problem, I think it's an OS problem. I can only describe my observations in non-technical terms:

I think the first tap draws the OS's attention to the touchpad, and the second tap does the job - activates the link, ect.

I believe it is an OS problem. All the things I have done by following the directions in this forum and the directions of the Launchpad.net helpers - it all helps some, but I still must tap twice most of the time. 

Anyone else have still have this problem?  (Dell Inspiron 1300)

---

### Post by ubu fubar on 2007-03-02
It's not an OS problem, more a driver configuration problem. The driver installs some (generally) sane defaults, but it's the same driver for all distributions and all synaptics touchpads, so the defaults are quite conservative.

Take a look at the [man page for the synaptics driver]("http://www.die.net/doc/linux/man/man5/synaptics.5.html") to see what configuration options are open to you. Notice how many there are?

To apply any of these settings just add them to the

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
        ......etc...............
EndSection

```

as ```
Option  "option"  "parameter"
```

lines. See [here]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Edit_xorg.conf") for an example of editing xorg.conf.

From your description it would appear that tap-to-click is not sensitive enough, so I would experiment with MaxTapTime, ClickTime, FingerHigh and FingerLow settings to begin with.

Remember to restart the X server to see the changes (ctrl+alt+backspace).

---

### Post by RichPicker on 2007-03-02
Thanks. Very interesting. I will experiment with them.

It seems like "True" and "On" accomplish the same thing. And it seems like it does NOT matter which order the "Options" are in.

---

