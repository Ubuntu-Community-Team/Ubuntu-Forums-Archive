---
title: "Customizing the gnome-panel clock's font."
date: 2009-05-26
forum: Art &amp; Design
---

### Post by t.rei on 2009-05-26
Hi,

on my venture of making my gnome desktop keeping up with recent improvements of looks-n-such of almost all other DEs, I have come to the point, where small things really matter a lot.

Customizing the gnome-clock i.e.

now, I have managed to choose a font by adding this to my theme's of choice gtkrc:
```
style "panel-clock"
{
  fg[NORMAL] = "#FFFFFF"
  font_name = "Droid Sans 18 Bold"
}
widget "*.clock-applet-button.*" style "panel-clock"
```The question I am having is: how do I figure out the name of the different fonts used therein? Is that possible?

i.e.:
```
style "panel-clock"
{
  fg[NORMAL] = "#FFFFFF"
  font_name = "Droid Sans 18 Bold"
}
widget "*.clock-applet-button.THE_CLOCK_FONT" style "panel-clock"

style "panel-clock-date"
{
  fg[NORMAL] = "#FFFFFF"
  font_name = "Droid Sans 14"
}
widget "*.clock-applet-button.THE_DATE_FONT" style "panel-clock-date"
```Thanks

---

### Post by Psyphre on 2009-06-06
I doubt its possible at all to change individual font aspects of the time. Thanks for the tip on changing the whole clock font tho.

---

### Post by Hemmer on 2009-11-10
Yeah you can do it. Theres a couple of neat blog posts about it:

[http://pijulius.blogspot.com/2006/05/gnome-panel-clock-applet-with-markup.html](http://pijulius.blogspot.com/2006/05/gnome-panel-clock-applet-with-markup.html)

[http://www.bomahy.nl/hylke/blog/pretty-gnome-clock/](http://www.bomahy.nl/hylke/blog/pretty-gnome-clock/)

---

### Post by Exodist on 2009-11-10
This thread needs a Sticky..

This is actually very good info for many of us that make themes and can help others in the future.

---

