---
title: "Custom Google Earth Icon Gnome"
date: 2009-08-27
forum: Art &amp; Design
---

### Post by hackerseraph on 2009-08-27
I made a custom icon for google earth and I want to include it in my icon pack. What do I have to name it and what folder in my pack do I have to put it in to make sure it gets called on gnome ubuntu 9.04?

I looked around on google, and looked in other icon packs but couldnt seem to come up with anything. Im begginning to think google earth wont call other icons >_>

---

### Post by motyR on 2009-08-27
ammm, u mean something like that?
grep Icon /usr/share/applications/<GOOGLE DESKTOP FILE HERE> | sed -e 's|.*=\(.*\)$|\1|'

and u should drop the file in the apps folder on each of the folders sizes 16x16,22x22 svg and so on.

---

### Post by hackerseraph on 2009-08-28
something like that lolz. your post actually helped me to figure out a bit more about ubuntu on my own. see by pointing me to /usr/share/applications/Google Earth

I learned thats where the "desktop icons" .launcher files are set up. I opened up google earth's launcher in gedit and learned its called googleearth in the icon pack. named my icon that, refreshed the gnome icon cache, and tada it worked. so in a round-about way, you saved the day. thanks :]

---

