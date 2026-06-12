---
title: "Screen resolution problems? Read this first:"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-10-28
Ok, I'm seeing a lot of posts with screen resolution problems, namely a chosen resolution won't stick, or there isn't a listing for the resolution you want.

Well, I had both of these problems, the latter first, and instantly I assumed the worst and most complicated, and started worrying about and fiddling with the drivers section of "Screens and Graphics", the new administration applet. And when I finally found the solution that was staring at my face the whole time (selecting the monitor model - there wasn't a GUI for that before Gutsy), I couldn't for the life of me get the new resolution to stick on reboot: the option for that is a simple checkbox in Preferences>Screen Resolution, to make the current resolution the default for this computer.

Now I'm sure there are many folks with a more complicated issue, but before you start fiddling around with xorg.conf, which does have some potential to mess up your installation, make sure you've tried these steps.

**System>Administration>Screens and Graphics,Screen Tab, Model**: There is a drop-down list for your manufacturer and model. Yes, it's obvious, but I must've clicked past it a dozen times while I went to try fiddling around with the Graphics card tab - that and there formerly wasn't a monitor selection list GUI before Gutsy. Once I selected my specific monitor instead of the default "Generic", a ton of new resolutions opened up for me. 

**System>Preferences>Screen Resolution, Options "Make default for this computer"** Simply selecting your resolution from the Screens and Graphics menu isn't good enough - you have to lock it in as your user preference with this checkbox. Again, maybe obvious, but easy to overlook if you've been focused on the new "Screens and Graphics" menu simply trying to get your desired resolution for the last few hours.

And if you don't have these options in your System menu, remember to go to System>Preferences>Main Menu. And if you don't have Main Menu in your System menu, then may God have mercy on your soul.

---

### Post by ofb on 2007-10-28
It's probably worth mentioning that people with the proprietary Nvidia driver installled also have a nvidia-settings GUI. (Just run 'nvidia-settings' in terminal to launch.)

Typically I use the Gnome interface to set my initial resolution, but then need to use nvidia-settings to get a better refresh than 75. Also nvidia-settings correctly autodetects my monitor, while Gnome doesn't include this model in its list.

So YMMV, but yes, do hold off messing with xorg.conf.

I note Gutsy has carried forward the bug that shows the wrong refresh rate in the Gnome panels after Nvidia is installed. (Typically 51Hz, an obvious fiction.)

---

