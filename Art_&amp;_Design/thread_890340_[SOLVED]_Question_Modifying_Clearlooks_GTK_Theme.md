---
title: "[SOLVED] Question: Modifying Clearlooks GTK Theme"
date: 2008-08-14
forum: Art &amp; Design
---

### Post by the yawner on 2008-08-14
I've been using Clearlooks Human Compact from [this theme pack]("http://gnome-look.org/content/show.php/Compact-Colors?content=78182") and lately I've been doing some small modifications mostly by trial and error.

So far I got the metacity theme (Clearlooks Compact Metacity) that's on default 

[IMG]http://img.photobucket.com/albums/v90/kiel_008/Screenshot-metacity-theme-viewer-1.png[/IMG]

to look like the this

[IMG]http://img.photobucket.com/albums/v90/kiel_008/Screenshot-metacity-theme-viewer.png[/IMG]

It somewhat mimics [Gommoso]("http://gnome-look.org/content/show.php/Gommoso?content=75530") which is actually also included as a metacity port included in the above mentioned theme pack. However, the hover and pressed button states are still the same as default metacity theme included in the pack.

Now my next attempt is to modify the windows list applet appearance and I'm not sure how to start as I've got little to work on the panel.rc file. Basically, I wanted to mimic the Xfce tasklist applet as shown below:

[IMG]http://img.photobucket.com/albums/v90/kiel_008/Xfce-Panel.png[/IMG]

Note that is only achieved in Xubuntu as the Xfce applet has an appearance option to use flat buttons. My question is, *is it possible to mimic this behavior in Gnome?*

---

### Post by smartboyathome on 2008-08-15
I am pretty sure it is. Take a loot at the GNOME theme link in my sig, and look for other themes which seem to do what you want.

---

### Post by the yawner on 2008-08-15
Thanks! I'll give it a shot.

Edit:

From this [post.]("http://ubuntuforums.org/showpost.php?p=5605157&postcount=711")
> **perfectska04@hotmail.com said:**
> Flat buttons should be really easy to get in GNOME without having to modify any theme. Just right click a panel, and select "properties". In the Background tab, choose a background image you would want to use for your panel, and as a result, unfocused items will not look like a button, but part of the panel itself.

Worked as expected. :)

---

