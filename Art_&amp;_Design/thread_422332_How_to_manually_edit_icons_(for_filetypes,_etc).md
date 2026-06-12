---
title: "How to manually edit icons (for filetypes, etc)?"
date: 2007-04-25
forum: Art &amp; Design
---

### Post by craigyjack on 2007-04-25
Hey,
I was wondering what is an easy way, if there is any, to edit the icons for say the default folders, or mountpoint, or trash? I know icon sets can do this, and I have an icon set, but I would like to be able to go in and manually change icon types (decently easy if possible) for the generic folder icons, or trash icon, etc.

I do not know how to make icon sets, and would rather not. I would rather just edit my current one, and change some icons that I do not like so much, with some images i like more (these are png's). Also, on a side note, their doesnt seem to be all that many icon sets from gnome really (i looked at gnome-look.org and art.gnome.org). And manually editing icons for an entire type of filetype (like mp3s, or folders, etc) isnt that easy, and that surprises me because of the level of customization of the desktops.

If anyone could offer me any help on how to get some of my own chosen icons into the general icons in use, I would greatly appreciate it.

Thanks,
Craig

---

### Post by tom56 on 2007-04-25
Icons are stored in /usr/share/icons/ or ~/.home/. You can edit svgs with Inkscape and all other image files with the GIMP.

---

### Post by craigyjack on 2007-04-25
But I want to replace the icons in the icon theme with my own icons, not just edit the current ones. Should I just replace the file with the same name? but also, I have pngs, not svgs, so the naming would prob mess up then. garrr

---

### Post by srhlefty on 2007-04-25
I think Inkscape can vectorize bitmaps.  The menu option is something like "trace bitmap"

---

### Post by kpolice on 2007-04-25
Just replace the icons you don't like and use the same name.

Also replace the icons with one of the same size.

It doesn't matter if the original is svg, you can replace it with a png.

---

### Post by craigyjack on 2007-04-26
Ok thanks, I will do that. mucho gracias.

Also, does anyone know a good set of dark icons (like goes well with a dark theme). I have searched through gnome-look.org and have yet to find a good dark one. There actually doesnt seem to be all that may icon themes at the site really, compared to the gtk, metacity, etc themes.

Thanks,
Craig

---

### Post by craigyjack on 2007-04-28
ahhh. I can't figure this out. I tried what you guys said. I am using an icon theme, so I went into the .icon folder and then the theme's folder, and replaced the .svg image there with my own .png image. I renamed the file the exact same name, but then it won't work.

For instance, I replaced the gnome-dev-removable.svg  with my own  gnome-dev-removable-usb.png. But when I stick in a usb device, the png isn't displayed, it's just a white looking rectangle (because the old .svg isn't there anymore). I thought you said you could replace a .svg with a .png and it would be okay.

Why is it so hard to change the icons used for a whole type of file, or folder or something??? Changing the icon for one folder, or one file, or launcher is super easy and i love that about ubuntu! I would have expected it to be that easy to change the icon for an entire filetype or folder in general (versus just one individual file/folder) but I have yet to have seen anything that makes it easy like that. I would like to be able to change my icon theme (specific icons in the theme), without just accepting a whole theme just as is. I love the customization of ubuntu (gnome really), and I'd like to know how to edit my icon theme so I can use my own altered theme.

I would appreciate your guys' help so much.
Thanks,
Craig

Also, I have tried converting my .png to .svg's with minimal success. They turn out really bad looking. I tried using inkscape(potrace) and autotrace, i messed around with a lot of options in inkscape, but i couldnt get the svg to turn out decently looking as the png is.

---

### Post by kpolice on 2007-04-28
It works for me.

Just remember in some icon themes there are icons for different sizes so you have to replace every size.

---

