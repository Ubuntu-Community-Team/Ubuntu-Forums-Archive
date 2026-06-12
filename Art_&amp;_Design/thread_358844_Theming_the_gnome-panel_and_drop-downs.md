---
title: "Theming the gnome-panel and drop-downs"
date: 2007-02-11
forum: Art &amp; Design
---

### Post by TravisNewman on 2007-02-11
I have a theme that I'm in love with, but...

some things are annoying me with it. I've tweaked it some, but I can't seem to tackle drop down menus and the gnome panel. Here are my two big issues.

In ff.png, you can see that the drop down menu there, doesn't match the other menus, such as the main menu as seen in the applications menu (menu.png).

Basically, I want to make those drop down boxes have white text and I can't find the variable for it.

I'd also like to have all of the gnome-panel be the same color of grey as is in those menus, but I can't seem to figure out how to change the gnome-panel without changing other things.

I've never tried custom theming with gnome before, so forgive my noobishness :)

Any hints?

---

### Post by bvc on 2007-02-11
what theme is it?
The same thing happens to my [MurrinaStyle]("http://gnomethemes.org/?p=52") theme in firefox. Firefox is not pure gtk, it is gdk>gtk so it can be difficult to impossible to fix things like this, and I gave up on ff long ago.

Link to the theme [EDIT: is it MurrinaFancyCandy?] and if someone doesn't already know, I'll take a look.

---

### Post by TravisNewman on 2007-02-11
> **bvc said:**
> what theme is it?
The same thing happens to my [MurrinaStyle]("http://gnomethemes.org/?p=52") theme in firefox. Firefox is not pure gtk, it is gdk>gtk so it can be difficult to impossible to fix things like this, and I gave up on ff long ago.

Link to the theme [EDIT: is it MurrinaFancyCandy?] and if someone doesn't already know, I'll take a look.

It is indeed MurrinaFancyCandy, with the grey color for the menu taken from MurrinaStyle. The issue that I'm having in Firefox also happens in Epiphany as well, and in kazehakase, so it's not Firefox specific. Though I do hate Firefox theming issues (the reason I'm not using plain MurrinaStyle is because Firefox didn't like it at all).

EDIT:
Murrina Fancy Candy: [http://cimi.netsons.org/pages/murrine/themes.php](http://cimi.netsons.org/pages/murrine/themes.php)

---

### Post by bvc on 2007-02-11
Well, I tried and can't get any change. Sorry.

---

### Post by kpolice on 2007-02-12
So you want the Applications/Places/System applet to be grey instead of blue? That can be done.

---

### Post by Albi on 2007-02-12
Not sure about these things, but if you can't find it, a good way is to open the screenshot in gnome, use the color picker, note the hex value, and search for it in the theme config file.  Just remember to add the slashes (eg. in gimp white would be ffffff, while in the file it would be ff/ff/ff)

---

### Post by s26c.sayan on 2007-02-15
> So you want the Applications/Places/System applet to be grey instead of blue? That can be done.
 		  			 			 				

How???? :)

---

### Post by TravisNewman on 2007-02-16
I'd like for app/places/system AND the rest of the panel to be grey. BUT not other widgets. But I'm not sure if that's possible.

And I also want to fix it so that text in drop down boxes is white. All drop down boxes are like this unless their colors are explicitly defined (as in some websites)

---

### Post by bvc on 2007-02-17
for the menu-bar```
style "panelbutton"
{
  bg[NORMAL]				= "#e7e7e7"
}
widget "*PanelWidget*" style "panelbutton"
```

---

