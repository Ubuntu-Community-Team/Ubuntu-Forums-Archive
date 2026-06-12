---
title: "iBook G3 - pbbuttonsd"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by David Starling on 2008-10-16
I'm trying to get power management to work on my iBook G3 (dual USB model) with Ubuntu 8.04. Specifically, I want to be able to get the keys on the top row to work like a Mac and be able to turn off the backlight on the LCD without putting the computer to sleep.

Ubuntu installs pbbuttonsd by default. This program seems to be working. For instance, if I type in the terminal "pbbcmd ejectcd" the CD tray ejects. And I can open the "powerprefs" program, but no changes I make there are saved. And, the keys on the top row are not changing the LCD brightness or ejecting the CD, they are doing the default shortcuts set by ubuntu (i.e. F1 opens the help viewer, F12 "right clicks").

I can get the computer to sleep properly by clicking the Red button on the top panel and selecting sleep. And the screen saver does come on after 10 minutes, but the LCD backlight does not turn off after the 11 minutes I selected. And when I close the laptop, there is no change.

Thanks in advance for your help!

---

### Post by jackoverfull on 2008-10-16
are you opening powerprefs as root?

---

### Post by David Starling on 2008-10-16
Oh brilliant! Yes, now it works. I can change the LCD backlight power with F1 and F2. Powerprefs still doesn't seem to be turning off the backlight after the timeout I give it. Do you have any experience with powerprefs? I feel like I'm just not understanding how it works.

---

### Post by jackoverfull on 2008-10-17
well, powerprefs is only a gui for the pbbuttonsd configuration file…
i had some experience with it a couple of years ago (that's why i remembered that it had no problem being totally useless if launched by a normal user…;)), but i didn't try to set a timeout…

I'm looking at the man pages ([1]("http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.html"), [2]("http://pbbuttons.berlios.de/projects/pbbuttonsd/man-pbbuttonsd.cnf.html")), in the first there is something abut a timer, but it doesn't seem to be internal of pbbuttonsd. Anyway, i'm sure that it is possibile to rely on some other software that can launch a script after a certain amount of idle time (a script that calls pbbuttonsd…). No idea of a such software, tought it surely exists.

---

### Post by kahsheung on 2008-11-15
Hi...Any updates on this?

I have an iBook G3 as well and I've installed Ubuntu 8.04. Some how the screensavers doesn't work or the power management settings can't turn off the monitor. Not even when I close the lid even though I've already set it.

All it does is render the screen with streaks of brown n black ( the majority of the color on screen) and just get stuck there whenever the time is up to turn off display or run screensaver.

Help please?

---

