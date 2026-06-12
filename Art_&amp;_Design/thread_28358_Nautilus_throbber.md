---
title: "Nautilus throbber?"
date: 2005-04-19
forum: Art &amp; Design
---

### Post by mark on 2005-04-19
I searched for this & didn't find anything...

Has anybody figured out how to replace the Nautilus "foot" throbber with a version of the Ubuntu logo?  I replaced the menu bar icon with the logo, but I've seen nothing on the throbber...

*Thanks!*

---

### Post by bored2k on 2005-04-19
[QUOTE=mark]I searched for this & didn't find anything...

Has anybody figured out how to replace the Nautilus "foot" throbber with a version of the Ubuntu logo?  I replaced the menu bar icon with the logo, but I've seen nothing on the throbber...

*Thanks!*[/QUOTE]
 Define throbber  :???:

---

### Post by benplaut on 2005-04-19
[QUOTE=bored2k]Define throbber  :???:[/QUOTE]

in nautilus browser mode, there is a small foot that's toes "throb" when the program is busy... sorta like the big E in internet explorer

I think ot chnage that you would have to go into the code of Nautilus... but i'm not sure

---

### Post by bored2k on 2005-04-19
[QUOTE=benplaut]in nautilus browser mode, there is a small foot that's toes "throb" when the program is busy... sorta like the big E in internet explorer

I think ot chnage that you would have to go into the code of Nautilus... but i'm not sure[/QUOTE]
 A foot ? well , after I changed my theme to Bluecurve icons, I get little circling dots, not the throbber. Maybe if we could find this custom image I'm saying we could figure out how..

---

### Post by Nis on 2005-04-19
[QUOTE=bored2k]A foot ? well , after I changed my theme to Bluecurve icons, I get little circling dots, not the throbber. Maybe if we could find this custom image I'm saying we could figure out how..[/QUOTE]
 Check out /usr/share/icons/hicolor/36x36/apps  There you'll find the throbber.

---

### Post by bored2k on 2005-04-19
[QUOTE=Nis]Check out /usr/share/icons/hicolor/36x36/apps  There you'll find the throbber.[/QUOTE]
 Yes but I can't seem to find my Bluecurve animation ... weird.

---

### Post by benplaut on 2005-04-20
[QUOTE=bored2k]Yes but I can't seem to find my Bluecurve animation ... weird.[/QUOTE]

i think it would be in a specific folder for that theme (not sure if that sort of thing exists, just guessing...

---

### Post by bored2k on 2005-04-20
[QUOTE=benplaut]i think it would be in a specific folder for that theme (not sure if that sort of thing exists, just guessing...[/QUOTE]
 I have searched for it in /usr/share/icons/Bluecurve , but I can't find it :@.

---

### Post by TravisNewman on 2005-04-20
it would probably be named the same as the foot-- have you tried searching for the filename of the gnome foot?

---

### Post by bored2k on 2005-04-20
[QUOTE=panickedthumb]it would probably be named the same as the foot-- have you tried searching for the filename of the gnome foot?[/QUOTE]
 Actually, bluecurve icons have different filenames. I know because a couple of days ago I was juggling to create a custom icon set.

---

### Post by kanem on 2005-04-20
Mine is called 'gnome-spinner.png' and 'gnome-spinner-rest.png'. They are in .icons/iconthemename/24x24/apps. Although they could probably be in 48x48 or 96x96 or whatever. 

The 'gnome-spinner-rest.png' is the icon that is usually visible. When stuff is going on you see the other one. I have themes that didn't have their own throbber, and all I had to do was put the appropriate icons with these names in the directory mentioned above. The 'gnome-spinner.png' is kind of strange though. It looks like 12 smaller pictures merged into one. When it is 'spinning' it is cycling through these.

---

### Post by link on 2005-04-20
Correct, so to make a gnome-spinner file, you need to build the series of static images. GTK+ then will roll over that pixbuf, displaying each image. I've got about a 1/2 working gnome-spinner of the Ubuntu logo working. Its still not quite right though. Maybe I'll pick it up again. :)

---

### Post by mark on 2005-04-20
[QUOTE=link]Correct, so to make a gnome-spinner file, you need to build the series of static images. GTK+ then will roll over that pixbuf, displaying each image. I've got about a 1/2 working gnome-spinner of the Ubuntu logo working. Its still not quite right though. Maybe I'll pick it up again. :)[/QUOTE]
Please post when/if you do.  I'm one of those "graphics-challenged" folks that can't seem to do anything with *any* kind of image...

---

### Post by kassetra on 2005-04-20
[QUOTE=link]Correct, so to make a gnome-spinner file, you need to build the series of static images. GTK+ then will roll over that pixbuf, displaying each image. I've got about a 1/2 working gnome-spinner of the Ubuntu logo working. Its still not quite right though. Maybe I'll pick it up again. :)[/QUOTE]

mine's done... it actually makes the logo dance around like people... but I collapsed it onto a white background... so it's not transparent... and I haven't bothered redoing it.

---

### Post by nautilus on 2005-04-20
I have to insert my post into this thread, since the topic got my attention...

And despite the issues discussed, I indeed DO throb with Ubuntu.

---

### Post by benplaut on 2005-04-21
[QUOTE=nautilus]I have to insert my post into this thread, since the topic got my attention...

And despite the issues discussed, I indeed DO throb with Ubuntu.[/QUOTE]

you are sooooo predictable  :roll:

i saw this reply coming a mile away  :razz:

---

