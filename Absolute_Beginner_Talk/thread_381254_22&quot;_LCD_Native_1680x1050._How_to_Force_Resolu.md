---
title: "22&quot; LCD Native 1680x1050. How to Force Resolution?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by wickedhund on 2007-03-10
I have a ViewSonic VX2245wm, 22" LCD.  I also have an nVidia 7600GT card.  Problem is, I have already installed the nvidia X-Server settings, and still i get a pop-up screen which says (as i already know) that my native screen resolution is 1680x1050.  The highest I can get on the Screen Resolution Preferences is 1024x768 @ 75 Hz.  I don't mind the 75 Hz, but i would like to see this gorgeous screen at its native resolution.  Any good code out there to force the resolution, so that I can still have a screen after the next reboot?

Thanks!

	8-[

---

### Post by tribble222 on 2007-03-10
Look at your /etc/X11/xorg.conf

There's a bunch of stuff in there.  There will be a few places in there that show 1024x768 among other resolutions.  You need to follow the pattern and add 1680x1050 to it.  OR just replace every instance of 1024x768 with 1680x1050 if you don't care about having the 1024x768 resolution option.

*make a backup of your xorg.conf before you mess with it*

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Once you've edited it you need to restart X.  Either hit ctrl-alt-backspace, or run

sudo /etc/init.d/gdm restart

in the terminal.

---

