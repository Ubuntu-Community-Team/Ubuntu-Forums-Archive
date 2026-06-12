---
title: "Still a small problem..."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-05-16
Hi again folks, I been still playing around with my theme (just found a super cool new login screen for my custom black theme). Since I am using a dark theme, I was having problems with firefox and open office. I fixed my firefox problem by replacing a simple file. I still seem to have a problem with open office though.

Here is the trouble, my open office icons at the top of the program are stuck in high contrast it seems. I am using smoked glass (GTK theme) with  a modified New Ale (emerald) theme. This is the instructions I followed:

[QUOTE=Instructions]Open Office 2:
------------
For dark themes Open Office 2 uses a high contrast icon theme (due to automatic icon settings). If you don't like this, do the following:

1. Open Tools -> Options dialog

2. Go to OpenOffice.org -> View

3. Change the icon theme from automatic/null to a different one.[/QUOTE]

See [pic]("http://i22.photobucket.com/albums/b324/FFManiac1/Screenshot-2.png") for what I mean, so I have tried switching to them all and nothing seems to change. I even reinstalled to the latest 2.2.1 release of OO but no change. What I do find interesting is that to the left I can pick large instead of small and the icons refresh and they change.

Is there a manual way to override whatever icon set is in use? Am I doing something wrong with the instructions? Do I have to deactivate Beryl to get this to work? anyone else have a fix for my problem, its the only issue I am having now with my Ubuntu setup, any help is appreciated a lot in advance :D

---

### Post by Happy_Man on 2007-05-16
Have you tried either Industrial or Crystal yet? Perhaps those will work...

---

### Post by starcraft.man on 2007-05-16
> **Happy_Man said:**
> Have you tried either Industrial or Crystal yet? Perhaps those will work...

Yeah, I went through all 5 different options, even restarted OO after I did, didn't seem to do anything... Do I have to restart my computer to get it to change? Shouldn't it just switch on the fly? Can Beryl get in the way (seems unlikely since it changed to large icons with beryl on)?

---

### Post by Happy_Man on 2007-05-16
Well, it seems you have to hit "OK" after changing the box. At least, for me. I'm sure you tried this, but I have to make sure...

---

### Post by starcraft.man on 2007-05-16
> **Happy_Man said:**
> Well, it seems you have to hit "OK" after changing the box. At least, for me. I'm sure you tried this, but I have to make sure...

Ya, the odd thing about it is when I push OK, the icons flicker (signalling their resetting) but then they reload the high contrast black icons. I've tried that for all the entries and all end up with the high contrast. I'm sure its something stupid I'm missing.....

---

### Post by Happy_Man on 2007-05-16
Perhaps it's a theme issue.... somehow, my gut is telling me OO.o isn't the problem here.

---

### Post by starcraft.man on 2007-05-16
> **Happy_Man said:**
> Perhaps it's a theme issue.... somehow, my gut is telling me OO.o isn't the problem here.

I was thinking that too... is there a way to manually exempt OO from the dark theme if thats the issue?*looks over in direction of super experienced staff folks for a bit of help fixing this*

---

### Post by Happy_Man on 2007-05-16
> **starcraft.man said:**
> I was thinking that too... is there a way to manually exempt OO from the dark theme if thats the issue?*looks over in direction of super experienced staff folks for a bit of help fixing this*

Super experienced staff folks use fluxbox and Gedit. They forgot this stuff years ago... :razz:

---

### Post by starcraft.man on 2007-05-16
> **Happy_Man said:**
> Super experienced staff folks use fluxbox and Gedit. They forgot this stuff years ago... :razz:

Noooooooooooooooooooooooooo.... awwww, someone has to be able to help lil old moi? Come to think of it, wheres taurus, he usually pops in out of no where right before I post things? Usually with the best answer too >.>

---

### Post by celafon on 2007-08-20
Hey!
I got that problem too. Have you managed to resolve this?

I also noticed an option in OOO but it does not seem to work:

Options->OpenOffice.org->accesability stuff (don't know english translation for this entry).

Anyway it states something like: Detect High Contrast Settings automatically.

It would be the thing to uncheck (it is checked by default), but it does not work at all....

I am not using OOO that much but this thing drives me nuts! :)

---

### Post by Tasu on 2008-02-23
Hmmm! Even I'm experiencing the same issue, the theme I use is ONUX, from gnome-look.org, and every change I make to the view, it just reverts back to high contrast... really annoying knowing that I can't edit this bit of my distro of choice! O_O ^_^

---

### Post by dejvor on 2008-05-18
Hi everybody!
Had the same problem with icons in OO.org (they were always high contrast). After many sleepless night managed to find a solution. It so easy it scares me: try "lightening" the black color in your color set under Appearance manager (select the current theme, click customize,select the Color tab, under Windows background click on the color and set the black color to a lighter tone (=more towards the gray, easily done by rising the Value value / usualy the value of 16 should do). Try this: have the OO window open beneath the Appearance manager window and change the Value value, you should see the icons in OO change as soon as the value reaches 16. Simpler than that...
Guess it's an OO feature of high contrast recognition (althought it's turned off in my case!). Guess if you use black you might as well be blind :)

Hope it helps!=D>

---

### Post by hellomoto on 2008-05-19
I would like to confirm the solution for this too.

It appears to be a bug in open office. Even the latest version 2.4.0

There is an option to turn "detect high contrast settings off." However as other people have said, this does not work. Even after closing and restarting etc.

There is a cut off point in your background colour were open office will automatically revert to high contrast mode.

Your windows background color needs to be higher than #262626 - So the darkest background you can have is #272727 without open office automatically reverting to high contrast mode. 

I consider this a work around as you should have the option to turn off high contrast mode.

It is worth nothing that whilst in high contrast mode you lose a number of functions from open office including: icons, and the ability to format cell colours.

If anyone finds a solution to this please post it here. Has anyone tryed compiling open office from source, maybe this would resolve the issue?

---

