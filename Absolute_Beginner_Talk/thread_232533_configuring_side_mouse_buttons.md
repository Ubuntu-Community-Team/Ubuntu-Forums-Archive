---
title: "configuring side mouse buttons"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-08
How might I go about configuring the side buttons on my mouse? I tried a general search in the package manager, but I'm not really sure what I'm looking for. It's a Microsoft mouse, but I don't know if that matters. Mainly I'd like to get the backwards/forwards functionality while using Firefox.

Thanks.

---

### Post by hopstah on 2006-08-08
it's going to come down to you editing your /etc/X11/xorg.conf file and adding or changing lines in the mouse section.  for example, i have a logitech mouse which has a thumb button that i have assigned to be a back button in firefox.  the relevant section in my /etc/X11/xorg.conf file is this: ```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"ButtonMapping"		"1 2 3 6 4 5"
EndSection
```

the zaxismapping takes care of the scrolling with the wheel, and the emulate3buttons turns the wheel button into a middle click.  but buttonmapping for me is what i needed to get the back button working.

if you search the forums for other xorg.conf files for mice, i'm sure you'll be able to get yours working just fine too.

---

### Post by JohnJSal on 2006-08-08
Thanks. But how did you figure out what numbers to put there?

---

### Post by Drakkor on 2006-08-08
I tried that stuff,but just decided to enable mouse gestures in FireFox.

---

### Post by hopstah on 2006-08-08
well, i learned most of my config crap through gentoo, which was a chore in itself.  a lot of it was trial and error, and a lot of it was reading threads on here and on gentoo's forums site.  i think there's a line that's something like ```
Option    "Buttons"    "(number)"
``` that you can put in there to try.  but you might want to try setting the Button Mapping variable to "1 2 3 6 4 5 7" or "1 2 3 6 7 4 5" and see what happens there.

---

### Post by JohnJSal on 2006-08-08
I tried adding the "Buttons" option and then running

/etc/init.d/gdm restart

but it said "failed" during the starting phase. So I don't know what happened now. Nothing seems different, and the buttons still don't work.

I assume that the numbers represent the buttons on the mouse. I already have a line in my file called

Option		"ZAxisMapping"		"4 5"

which apparently sets up the scrolling. I would have figured that buttons 4 and 5 are the side buttons, but now I'm not so sure (I have a 5 button mouse).

---

### Post by JohnJSal on 2006-08-08
> **Drakkor said:**
> I tried that stuff,but just decided to enable mouse gestures in FireFox.

I definitely have that too, but it's amazing how much I rely on that back button! :)

---

### Post by jimrz on 2006-08-08
> **JohnJSal said:**
> How might I go about configuring the side buttons on my mouse? I tried a general search in the package manager, but I'm not really sure what I'm looking for. It's a Microsoft mouse, but I don't know if that matters. Mainly I'd like to get the backwards/forwards functionality while using Firefox.

Thanks.

here is the mouse section from my /etc/X11/xorg.conf:

```
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection
```

this gives me the functionality you are looking for with my MS 5-button mouse

---

### Post by JohnJSal on 2006-08-08
That works! Thank you!

Of course, there's no telling which other combinations I tried worked, because I only just now tried resetting my computer after making the changes, and that's what did it. The other method of restarting the window manager didn't seem to work.

---

### Post by jimrz on 2006-08-08
> **JohnJSal said:**
> That works! Thank you!

Of course, there's no telling which other combinations I tried worked, because I only just now tried resetting my computer after making the changes, and that's what did it. The other method of restarting the window manager didn't seem to work.

you're more than welcome. I had issues with this when moving from Beerzy to Dapper. Seems they rearranged the numbering with the advent and popularity of side scrolling wheel mousees. Found the answer right here on this forum...just passin' it along.

---

### Post by JohnJSal on 2006-08-09
Yeah, and I didn't realize that scrolling up and down was considered two separate 'buttons', so a 5 button mouse actually maps 7 buttons!

---

