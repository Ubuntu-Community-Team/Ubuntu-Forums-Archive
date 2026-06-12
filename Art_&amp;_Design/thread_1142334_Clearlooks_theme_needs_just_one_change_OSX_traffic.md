---
title: "Clearlooks theme needs just one change: OSX traffic light buttons"
date: 2009-04-29
forum: Art &amp; Design
---

### Post by hobo14 on 2009-04-29
Clearlooks, Human and similar theme's windows are fine, I'm content, except for the window buttons (minimise, maximise, close) ; ugly and old-school, IMHO.

I'd really like OSX traffic light buttons instead, but every OSX theme I find also seems to lock the window title bar to grey, which I don't want.

Does anyone know of a theme that has OSX buttons (right hand side) on a colour-changable window title bar? 
(OSX rounded blue scroll bars would be nice too, but not necessary)

Either that or maybe the current buttons are just image files that I could replace, if someone can tell me their location?

---

### Post by Saint Angeles on 2009-04-29
im really not a fan of the round buttons... but if you go to [www.gnome-look.org](www.gnome-look.org) , you will find SEVERAL themes with mac-style buttons and stuff.

---

### Post by hobo14 on 2009-04-29
Cheers SA.

Yes, I've been to gnome-look.org and tried quite a few OSX themes, but like I mentioned before, the all lock the window title bar to grey - I can't change it's colour.

---

### Post by morgengenuss on 2009-04-29
just edit the theme, it's really rather simple if all you want to change is the titlebar's background color... (you only have to replace a single image)

---

### Post by hansdown on 2009-04-29
Hi hobo14.

The thin ice theme is nice.

---

### Post by hobo14 on 2009-04-29
> **morgengenuss said:**
> just edit the theme, it's really rather simple if all you want to change is the titlebar's background color... (you only have to replace a single image)

I'm sure it is, as soon as you've done it once before.

For example, how would I make this Panther Metacity theme have colour-changable title bars?

[http://www.gnome-look.org/content/show.php/Panther?content=16320]("http://www.gnome-look.org/content/show.php/Panther?content=16320")
(This is my favourite theme with traffic light buttons: changes windows only, focused buttons show symbols, icon in the title bar, title bar colour has gradient from top to bottom)

It doesn't have an image for active window bars (and if it did what would I change it to?), so the colour must be set in the xml file.  
Which line do I need to change, and what do I change it to?

---

### Post by morgengenuss on 2009-04-30
> It doesn't have an image for active window bars (and if it did what would I change it to?), so the colour must be set in the xml file.
Which line do I need to change, and what do I change it to? 

how about what comes after "<!-- title bars -->" (LINE 43)

you can also go and look for a theme that uses an image...

---

### Post by hobo14 on 2009-05-03
> **morgengenuss said:**
> how about what comes after "<!-- title bars -->" (LINE 43)

you can also go and look for a theme that uses an image...

Ok, I change the three colour values, yes?  To what?

---

### Post by hobo14 on 2009-05-04
Hey seriously guys, I'd really appreciate it if someone would tell me what value to change the colours to in the xml file to make the titlebar color changable....

---

### Post by jorgecs10 on 2009-05-05
I suggest you to read this [tutorial]("http://live.gnome.org/GnomeArt/Tutorials/MetacityThemes")

---

### Post by hobo14 on 2009-05-05
Hey, cheers Jorgecs, I think there's enough info there for me to be able to do what I want, when I have time to try a few things out.

For anyone else with a similar problem to mine, use one of the following in place of a colour value:
gtk:base[NORMAL]
gtk:bg[NORMAL]
gtk:fg[NORMAL]
gtk:fg[SELECTED]
gtk:light[SELECTED]
gtk:dark[ACTIVE]
gtk:text[NORMAL]
Probably all combinations of the second and third elements will be ok (I havn't tried yet)

Eg: 
<color value="gtk:fg[SELECTED]">

---

### Post by hobo14 on 2009-05-10
Ok, I got round to editing the Panther theme, and the result is:

Windows with rounded corners, OSX traffic light buttons (RHS), user-changable colour (gradient light to dark), mini-icon infront of the title.

[http://www.gnome-look.org/content/show.php?content=104500]("http://www.gnome-look.org/content/show.php?content=104500")

There's also a version there with grey buttons.

---

