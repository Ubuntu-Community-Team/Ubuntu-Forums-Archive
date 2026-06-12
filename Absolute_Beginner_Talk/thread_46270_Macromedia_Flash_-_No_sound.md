---
title: "Macromedia Flash - No sound"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by xbilly on 2005-07-04
I get the flash animation but no sound in Mozilla.

I used "sudo apt-get install flashplayer-mozilla" in Root terminal



billy

---

### Post by sapo on 2005-07-04
just take a look here:
[http://ubuntuforums.org/showthread.php?t=43854&highlight=flash+sound+ln](http://ubuntuforums.org/showthread.php?t=43854&highlight=flash+sound+ln)

---

### Post by xbilly on 2005-07-04
Already did that. Still no audio

---

### Post by poofyhairguy on 2005-07-04
You want this command:

> killall esd

But you might notice that other sounds don't work then....

That is a big bug in hoary...and is the top priority for Breezy.

---

### Post by sapo on 2005-07-04
[QUOTE=poofyhairguy]You want this command:



But you might notice that other sounds don't work then....

That is a big bug in hoary...and is the top priority for Breezy.[/QUOTE]

good to hear it.. the thing that gives me more problems is ESD, it crashes a lot and have bugs with a lot of apps...

the only 3 things that crash here:
esd
nautilus
gnome-panel

---

