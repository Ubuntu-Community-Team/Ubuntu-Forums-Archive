---
title: "Metacity themes questions"
date: 2007-04-22
forum: Art &amp; Design
---

### Post by Fluxid on 2007-04-22
Hi!
I have two questions about making themes for metacity:

1. Can i change order of buttons on tittle bar, or, for example, move close button to the right?
2. Can i completely remove menu button (i don't mean to "draw nothing", i just don't want it at all)?
3. Can i make each button other size (for example like close button in windows vista)?

Thanks in advance for answers!

Fluxid

---

### Post by engla on 2007-04-22
1 is possible (what I know). Use gconf-editor (launch from terminal, it is hidden by default :( )
Go to 'apps > metacity > general > button_layout' in gconf-editor to change button order. the : separates the left and right side. My preference there is 'maximize,minimize,menu:close', but that's just an example. I guess if you omit one button, it is not drawn.

I don't know about 3 but perhaps you can find a special theme.

---

### Post by Fluxid on 2007-04-22
Thanks for that! I removed the menu :)
Anyway, is it a way to make it theme-dependent?

Now, what about other things... -_-

---

### Post by klausdiemaus on 2010-02-24
> **engla said:**
> 1 is possible (what I know). Use gconf-editor (launch from terminal, it is hidden by default :( )
Go to 'apps > metacity > general > button_layout' in gconf-editor to change button order. the : separates the left and right side. My preference there is 'maximize,minimize,menu:close', but that's just an example. I guess if you omit one button, it is not drawn.

I don't know about 3 but perhaps you can find a special theme.

Is it possible for the theme to set this without having to let users know how to change this?

---

### Post by londonali1010 on 2010-02-26
Hi Fluxid,

I'm not a Metacity expert, but have you read through the [Gnome Metacity tutorial]("http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html")?  It might get you what you want, although you'll probably have to modify the xml file...

---

### Post by days_of_ruin on 2010-02-28
> **klausdiemaus said:**
> Is it possible for the theme to set this without having to let users know how to change this?

No, it is a global metacity setting.

---

