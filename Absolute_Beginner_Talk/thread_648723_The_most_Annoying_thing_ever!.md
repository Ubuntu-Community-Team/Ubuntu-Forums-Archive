---
title: "The most Annoying thing ever!"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by PreviousN on 2007-12-23
Hey guys. I have a REALLY annoying problem. Well, when I first installed ubuntu, my keyboard was functioning perfectly. Then I installed desktop effects using envy. This worked perfectly, but one really annoying thing is that the keyboard will not work in nautilus/terminal (sporadically)/the desktop. 

For example, I'll make a new folder, and if I try to rename it I'll type  and nothing will type. Thus, I have a bunch of "untitled folders" on my desktop. The only way to rename it is to ssh in or open up a terminal and get lucky. 

Usually terminal works well but when I try to open like 5+ of them it stops accepting input form the keyboard. I at first thought it was an xorg problem, but have no clue. Short of reinstalling, any ideas? Heres a copy of the relevant section of my xorg, and a backup from a long time ago...

Current one...
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection
```

Old backup

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```

The problem is that with this setup (the backup), GNOME gives me an error on startup. Its something like "your xorg.conf settings don't match with what GNOME detected. What would you like to do? Use Xorg, or use GNOME's settings?"

No matter what I click on, the same problem happens... ie: it works for a while then stops. Is there some sort of autodetect keyboard utility? How do they detect keyboards on install? 

If I could get to the "detect keyboard" utility used for installs, that might fix my problem. Where is it/ what is the command?

Thanks!

---

### Post by spiderbatdad on 2007-12-23
have you checked out the keyboard preferences utility. It is highly configurable. Under layout you can choose to change to generic 101, maybe thats the one you want. idk for sure

---

### Post by PreviousN on 2007-12-24
Thanks. I hate you so much....That worked perfectly. And it was so ******* easy. I've been just "dealing" with this problem for about 2 and a half weeks now. 

Kudos to you. Thank you!

---

### Post by PreviousN on 2007-12-24
I take all of it back. It still has the bug. Maybe its related to compiz? I hope not! Ideas anyone? I'll post any info you want to help solve the problem!

Thanks...


Edited:

I tried disabling compiz. Still have the problem. LIke I said earlier...Is there a way to get to a keyboard detector like in the installer?

---

