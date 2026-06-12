---
title: "Adjust theme so buttons are smaller?"
date: 2007-07-08
forum: Art &amp; Design
---

### Post by OneSeventeen on 2007-07-08
I downloaded a nice looking theme that emulates OSX Leopard but many of the buttons are just too huge.  In fact, they are so huge I can't use inkscape because all of the buttons don't fit on my screen.  Here's a screenshot:
[img]http://bin.woventhorns.com/large_buttons.png[/img]

I'm poking around the gtkrc file for the theme, but I can't seem to figure out what needs to change to modify the spacing.

---

### Post by crimesaucer on 2007-07-08
Can you post your gtkrc. I'll take a look, but I can't guarantee it since I usually only write themes for xfce xubuntu.

---

### Post by bvc on 2007-07-09
it's possible something can be done, but judging from the screenshot I'd guess...not in this case. Because the adjustments would be paddings and such in the gtkrc and the icon seems to fill the button indicating there's no extra padding specified in the gtkrc. Still, post it so we can look and see for sure.

---

### Post by maruchan on 2007-07-10
Another random way to do it ;)

1. Install Kubuntu (no, I'm serious)
2. Tell KDE to use its own fake-GTK widgets in System Settings -> Appearance
3. Start a GTK app
4. Boom, extra space all gone.

---

