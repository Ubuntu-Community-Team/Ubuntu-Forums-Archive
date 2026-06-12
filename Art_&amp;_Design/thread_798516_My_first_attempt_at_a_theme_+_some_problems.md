---
title: "My first attempt at a theme + some problems"
date: 2008-05-18
forum: Art &amp; Design
---

### Post by k99goran on 2008-05-18
I have a bit of a problem with a theme I'm working on. Nautilus seems to insist on using "fg_color" for the text while editing filenames. The "fg_color" is very similar to "base_color" which is used as background for input boxes.

Is there any way of fixing this?

The theme I'm working on is a modification of a theme called Sauna-Dark by emrah ünal. [linky]("http://www.gnome-look.org/content/show.php/Sauna-Dark?content=80633")

---

### Post by Xfcn on 2008-05-18
New colors is all I can think of...

---

### Post by k99goran on 2008-05-19
I messed around with it for a while and I couldn't change the settings, so I had to change the colors.

Anyway, I posted a new screenshot over at Deviant Art. I think it turned out ok. [linky]("http://theli-at.deviantart.com/art/Browner-Ubuntu-86015279")

---

### Post by Chokkan on 2008-05-19
I think this is fantastic. I'd love to have these colors on the Elegant theme I currently use.
Anyway, great work and I'm looking forward to a release.

---

### Post by malcolmb on 2008-05-19
Mmm...Coffee flavoured desktop.

---

### Post by oedipuss on 2008-05-20
Try looking into widget_class and widget style assignments. I think it's possible to override colors even for specific apps, this way. 
I imagine something like 
widget_class "*Nautilus*" style "fixed-colors-style"
or widget "*Nautilus*" etc
where that particular style would have a different fg_color set.
It would override all widgets belonging to a class with Nautilus somewhere on it, but you could narrow it down.

---

