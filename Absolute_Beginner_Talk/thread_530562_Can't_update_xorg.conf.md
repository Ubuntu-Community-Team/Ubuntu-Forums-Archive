---
title: "Can't update xorg.conf"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by doktarr on 2007-08-20
Hi all,

I have a Gigabyte NVIDIA GeForce 8400 video card, which I am using to output via DVI/HDMI to a Samsung DLP with 1280x720 resolution.

I used Envy to install the latest drivers for this card.  I have encountered two problems here (the first being a more major concern):

1)  When I use the NVIDIA utility to update my resolution from 800x600 to 1280x720, I can't save this configuration to xorg.conf.  It appears to be some sort of permission issue.  When I open xorg.conf in a text editor it is read only, as well.  I tried "sudo chmod 777 xorg.conf" but that didn't change anything.

2)  As soon as I run Envy, the fonts on the login screen become ridiculously small, such that I can't read what I type (and any error messages are illegible).  I haven't spent too much time worrying about this one and I might be able to find a workaround on my own.

---

### Post by Hobo Joe on 2007-08-20
Don't run the nVidia control panel through the menu, run it with this command:
```

sudo nvidia-settings

```
That will give you root permissions that will enable you to make changes to your xorg.conf.
If you want to run it from the menu, go to 'System > Preferences > Main menu' find the nVidia control panel, and change the command, and add the prefix 'gksu' to it.

---

