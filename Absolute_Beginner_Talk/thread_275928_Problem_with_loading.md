---
title: "Problem with loading"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by bob74 on 2006-10-12
Can only load when selecting video fail-safe mode.
Using alternate loaded onto HD dual boot with XP
but end up with a screenful of multi-coloured garbish.
If I go back to the CD in fail-safe mode and try install from there the program hangs at page3(keyboard setting).
It appears I have a graphics driver problem and I have tried downloading from nVidia the linux driver with no success.
I have tried from the console the"sudo apt-get......nvidia-glx"
which loads OK but"sudo gedit/etc/X11/xorg.conf" is not recognised as a command.
I have spent hours looking through threads seeing similar problems but none of the ideas put forward work for me. I can't believe I am alone with this particular fault.
Where am I going wrong?

---

### Post by Sirkent on 2006-10-12
Are you having problems loading a graphical environment from the CD, or is this on your actual installation of Ubuntu?

Ok, so you've installed the nvidia-glx driver. Your command to edit your xorg.conf appears to be slightly wrong - you're missing a space. It should be:
sudo gedit /etc/X11/xorg.conf

However, I'm assuming from the fact that you're using gedit that you're already in a graphical environment. If that's the case then the keyboard setting issue could still remaing after you've got the Nvidia driver working. Come back if that's the case and I'm sure someone can help you out.

---

