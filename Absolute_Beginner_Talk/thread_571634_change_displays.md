---
title: "change displays"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by tronnix75 on 2007-10-09
ok i checked the sound and the line in and some others where muted, ok sound works, ok what i want to do with the ATI drivers is what i do on Windows, i want to be able to play movies off my laptop to my Tv via S-video cable and headphone jack rca cable.  I usually use VLC and i know that is compatible with ubuntu linux how do i install VLC and then change displays? from using the ati graphics card. I do this in windows by going to the desktop properties and clicking on the TV button and then hit apply, how can i do this with ubuntu?

---

### Post by jfinkels on 2007-10-09
Hi! You can install VLC by typing in the terminal:```
sudo aptitude install vlc
``` Read the first link in my signature for more information on installing software in Ubuntu. Also take a look at the 'restricted formats' link, as you may need the package 'libdvdcss2' to decode encrypted DVDs.

As for switching your display, is there a button on your keyboard that allows you to switch between the built-in laptop display and an external display? On Dell computers, it's usually <Fn>+<F8> or something similar. It may say something like "CRT/LCD" or have a little picture of a CRT screen. 

If that doesn't work you may need to set up dual screens using multiple X displays, or by using Xinerama. I don't know much about that, so you'll have to search around for more information on that.

---

