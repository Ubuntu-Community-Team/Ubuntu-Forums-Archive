---
title: "Dang These oversized windows!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jaimerod on 2008-03-20
I'm having a bit of a problem. Its actually more of an inconvenience, but part of the joy of Linux is you can fix all those little in conveniences right? Okay, down to the nitty gritty.  When ever I open up windows, the window is just a little to big. Its bigger to the right and bigger on the bottom. The thing that I don't like about it is, I have to manually resize every windows to get it inside a single desktop. Otherwise it shows up on the desktop to the right and on the panel of that desktop as well.

Is there a way to set the default window size upon opening?

Thank you all for your help.  The Ubuntu community ROCKS!

---

### Post by chucky chuckaluck on 2008-03-20
have you ever tried a tiling window manager? once i got used to wmii, i've rarely gone back. [http://en.wikipedia.org/wiki/Tiling_window_manager](http://en.wikipedia.org/wiki/Tiling_window_manager)
they're great for managing with a keyboard, as well.

---

### Post by jaimerod on 2008-03-25
I tried the window manager you suggested wmii. But I really can't use it. I'm have very little desktop realty available and a tiling window manager only makes less available to me.  I checked the compiz manager hoping to find a setting to control the initial size of a windows upon launch, or define the size of initial size of windows when they are not maximized.

Does anyone have any tricks up their sleeves?

---

### Post by wolfen69 on 2008-03-25
that's usually an indication of wrong screen resolution. what size is your screen? what is it set to?

---

### Post by Therion on 2008-03-25
I'm not entirely certain I understand what you're seeing with this problem... Screenshot possible?

Maybe, if I understand your problem correctly, you could try using the **Place Windows** plugin in Compiz.  Open the plugin and you can choose from the following options to change how windows behave on opening:

[LIST]
[*]**Cascade** places windows in a cascade, starting from the top left hand corner of the screen.
[*]**Centered** places all windows in the center of the screen.
[*]**Smart** places windows to avoid overlapping other windows on screen as much as it can.
[*]**Maximize** places windows in the center, and maximized by default when placed.
[*]**Random** places windows anywhere in the work area.
[/LIST]
I'm thinking Maximized, or maybe Centered, might be your best option?  Hope that helps...

---

### Post by Fury5000 on 2008-03-25
There are many strings about this problem, its just finding the search terms people have called this problem in the past.  Some call it "window off center problem" "windows alignment problem"  I am surprised anyone is not familiar with this bug as I would call it.  I have installed Ubuntu 7.1 on over 70 pc's and never seen one that didnt have this issue right out of the box.  The systems I deploy are in a work environment so I turn off the "desktop effects" and this problem immediately goes away.  Its a compiz issue.  There are some workarounds as a previous poster has described.  I do wish the desktop effects were "off" by default on new installs so people could learn the OS and fall in love with it without some of the quirky/buggy things aggravating them from the start.  I was curious if this "issue" carried on to 8.04 beta and installed it the other day.  Still there.

---

### Post by jaimerod on 2008-03-26
I apologize if there were previous threads with this topic already made in this forum. However, I was unable to find them.  I tried to use the place window plugin but it didn't work. I look through all the rest of the plugins to see if there is any other option. Unfortunately as of now, I cannot find any fix for this.

---

### Post by apothecaryaaron on 2008-03-26
I'm going to throw up an idea for those more experienced...
 
I've never used it personally, but would **DevilsPie** be able to take care of this problem? It's probably an over-complicated workaround, but maybe someone who uses it will say otherwise.

---

### Post by Fury5000 on 2008-03-26
I did a quick search using some popular wording for this and came up with dozens of posts referencing this problem.  Here are a few from the past few days.  The last one is about using Devel's Pie as a work-around.  I truly don't see how this has gone this long without being addressed.  I wish I had saved the links to the "big strings" about this that went on for pages.  I had bookmarked them to keep checking every now and then if this issue was being worked on.  I believe the issue was related to apps not remembering the last positions used.  I stopped following them after just deciding to turn off compiz.  I told myself I would check to see if compiz was ready for prime time in the next release.  As I said before.  Ran Ubuntu 8 beta... still there.  How sad is that.



[http://ubuntuforums.org/showthread.php?t=713276&highlight=window+off+screen&page=2](http://ubuntuforums.org/showthread.php?t=713276&highlight=window+off+screen&page=2) 

[http://ubuntuforums.org/showthread.php?t=89627&highlight=window+positions](http://ubuntuforums.org/showthread.php?t=89627&highlight=window+positions)

[http://ubuntuforums.org/showthread.php?t=729214&highlight=window+off+screen](http://ubuntuforums.org/showthread.php?t=729214&highlight=window+off+screen)

[http://ubuntuforums.org/showthread.php?t=249002&highlight=partially+off-screen](http://ubuntuforums.org/showthread.php?t=249002&highlight=partially+off-screen)

[http://ubuntuforums.org/showthread.php?t=563709&highlight=partially+screen](http://ubuntuforums.org/showthread.php?t=563709&highlight=partially+screen)

[http://ubuntuforums.org/showthread.php?t=301186&highlight=partially+screen](http://ubuntuforums.org/showthread.php?t=301186&highlight=partially+screen)


HOWTO: Automating Gnome with Devil's Pie
[http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

---

