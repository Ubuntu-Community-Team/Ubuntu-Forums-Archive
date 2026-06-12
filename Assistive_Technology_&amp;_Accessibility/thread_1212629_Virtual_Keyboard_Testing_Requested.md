---
title: "Virtual Keyboard Testing Requested"
date: 2009-07-13
forum: Assistive Technology &amp; Accessibility
---

### Post by jacksonyee on 2009-07-13
Hey there, guys!

I've recently brought myself a new Motion Computing M1300 tablet, and of course, tried Ubuntu on it. I managed to get the hardware working well with the exception of screen rotation, and the next thing that I needed was a nice virtual keyboard so I could avoid carrying a USB keyboard with me.

I've tried several different keyboards, but haven't found one that I would prefer. Onboard is acceptable, but is a bit annoying to use the function and special keys. matchbox-keyboard works well on my N800, but doesn't have the right layout and ability to be dragged on a larger screen. Klavier wouldn't stay on top, and kvkbd (so close to being right) had too much separation between keys for stylus tapping and a non-bold font. None of the above had my other favorite feature of the N800's keyboard - word prediction.

Therefore, I threw together a quick keyboard using pygtk, cairo, and sqlite. This is currently only for us American English users, but does include nicely colored keys, an easily seen bold font, and word prediction from both the system dictionary in /usr/share/dict and the ability to add new words. If anyone has need of a virtual keyboard and wants to test this out, just download the attached file and click on the file called virtual-keyboard.

Things to do:
* Internationalization
* Loading layouts from different places
* Redo the "Add word" dialog in Cairo so that answering the dialog doesn't take away focus from the selected window

Suggestions, comments, and especially code patches are welcome.

---

