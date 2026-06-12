---
title: "Change power manager and volume applet icons"
date: 2006-10-30
forum: Art &amp; Design
---

### Post by JedTheHead on 2006-10-30
PLEASE HELP ME!!!!  I am losing my mind and have been chaning icons all over the place trying to track this down.  I don't want to use the Tango / default theme and I want to change the icons for the power manager and the volume control applets.  I have read several posts that speak for earlier versions of gnome, but NONE of them work.  Can someone please supply the definitive answer as to how to change these?!?!?

Thanks!!!

---

### Post by GazaM on 2006-10-31
Both applets can be themed by the icon themes themselves, so I'm guessing the one you want to use doesn't include any. If you have your own that's fine, just drop them in the appropriate directories in the theme you're using... eg. 'audio-volume-high.(png/svg)' goes in <icon-theme>/<size>/status/ and so on for the other volume applet icons. The power-manager icons (such as 'gpm-primary-charged' and so on) go in <icon-theme>/<size>/apps/ folder.

To get the appropriate names to use for the icons, just look at the existing ones. You can see the audio applet ones in most of the themes, such as gnome and Tango, and you can see the gnome-power-manager ones in either the hicolor theme or the Human theme (Human only provides 22x22 gpm icons iirc).

---

### Post by JedTheHead on 2006-11-01
I thought I had tried all that, but will do so again!  Thanks for the detailed response!!!

---

### Post by JedTheHead on 2006-11-02
Success!  It was the 22x22 and not 24x24 that did the trick.  Thanks again!!!

---

