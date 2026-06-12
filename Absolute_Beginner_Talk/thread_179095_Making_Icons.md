---
title: "Making Icons"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-19
I'm trying to create my own file icons and I'm not sure what I'm doing incorrectly.
There is probably an easier way to do this. But, I would like to know how to create my own icons. First I went [here]("http://ubuntuforums.org/showthread.php?t=129154&highlight=change+iconshttp://ubuntuforums.org/showthread.php?t=129154&highlight=change+icons"), but this looks complicated (maybe I'm just tired). I'm not sure what 'mime' means.

I don't like the blue thing for Mozilla Firefox, so I stole their logo and put it in .ico .png & .xpm at 48x48 in home/Pictures/Icons (a folder I made, obviously).

When I right click the blue thing and click to change the icon and go to home/Pictures/Icons, they are greyed out :(. I cannot select them to use them for icons.

I thought I'd be smart and move those icons to /usr/share/pixmaps, where all the other icon files are kept. That didn't work either, they don't show up at all in that menu. (I see them when I go to the folder itself, but not in the 'change icon' dialog menu.)

Is it even possible to create your own icons? I'll be really sad if it's not! If it is possible, what am I (not) doing?

Another quick question: I used ```
enzo@reboot:~/Icons$ sudo mv firefox1.5.xpm /usr/share/pixmaps
``` to move the file. What is the command to copy a file to a directory? (instead of moving the file altogether.)

---

### Post by richbarna on 2006-05-19
I see that in the repositories there is an Icon Editor, I haven't used it but I suppose there must be a "save icon" dialogue, and as it is designed for the Gnome desktop I imagine it will save them in the correct place.
> sudo apt-get install gnome-iconedit

---

### Post by Clay85 on 2006-05-19
Oh wow, this program is uber neat!

Let's see if I can work it. :)

Thank you. :D

---

### Post by Clay85 on 2006-05-19
I like it a lot!

When I close one window they all close, though. :(

---

