---
title: "Right-Click as a keyboard shortcut"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-03-17
There's a key, usually to the right of alt which in windows does the job of right-click.

How do i configure it to do the same thing here?

---

### Post by mlissner on 2007-03-18
Well, theoretically, it should already do the same this, but I guess that's not the case on your keyboard for some reason. 

I can think of three things to try:
1. Start by tinkering with the keyboard selection in the preferences. One of the different keyboards might just be configured correctly to make everything work.

2. Use xev and xmodmap
I think this is the most complicated method, but it's also the most reliable if you can figure it out. I failed at figuring this method out for my keyboard needs, but maybe you'll have better luck. The basic idea is this:
 - Install xev
 - Use xev to determine the code number for the button
 - Use xmodmap to remap the keysys called "Menu" (case sensitive).

3. Use xkeycaps (my recommendation)
xkeycaps tries to do the tricks of xmodmap and xev graphically, and worked pretty well for me. I believe it's in the Universe repo, but I'm not sure. The method for using it is this:
 - Install xkeycaps and start it via command line.
 - Configure the desired button to have a keysys of "Menu"
 - Write the new keymap to a file saved in your home directory (so the setting will be saved after reboot)

I think one of those methods will work, and if you go with method two, more power to you.

---

