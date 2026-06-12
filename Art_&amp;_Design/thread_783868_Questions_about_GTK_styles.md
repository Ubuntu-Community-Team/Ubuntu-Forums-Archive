---
title: "Questions about GTK styles"
date: 2008-05-06
forum: Art &amp; Design
---

### Post by maury84 on 2008-05-06
Hi! Actually I'm spending some time in the creation of GTK styles. I've designed everything, bars, window borders, buttons, etc...
But I don't understand a thing...Sometimes, using styles (even not mine, taken from gnome-looks for example...), when the style is not an "Ubuntu style" (like Clearlooks, Human, etc...) bars and icons are not applied on "root" windows, like, for example, on Synaptic. Infact, synaptic have different icons on the toolbar (most of times are clearlooks icons) and diffent windows decorations (progress bar, scrollbar, and similar...) Why? Is because the themes doesn't use a own engine? How can I fix it and use the icons and decorations of the theme I'm using?
Thanks to everyone!

Regards

Maurizio

---

### Post by marufaberlin on 2008-05-06
The styles are saved to the user configuration. So, as root is a different user, the style is a different one to. But you can change that.

---

### Post by maury84 on 2008-05-06
Uhm, ok! So for the main styles is different 'cause they are built in...And if I want to extend the theme to all users (including root) what I've to do? Use the share folder in filesys/usr??

Thanks

Maurizio

---

### Post by Half-Left on 2008-05-06
just create a folder in /root called .themes and put them in there.

> sudo nautilus --no-desktop to do it the UI way.

---

### Post by maury84 on 2008-05-06
Thank you so much! :)

---

### Post by smartboyathome on 2008-05-06
use gksudo for graphical commands. Also, copy all your icons to /usr/share/icons and all your themes to /usr/share/themes, and they will be used on all windows.

---

