---
title: "Default File Icons"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-11-27
Is there any way to change the default icon for a particular file type? Case in point I want all .mp3 files to have a different icon so that I can distinguish them easily (The right click properties dialog only changes single files).
Thanks

---

### Post by tocleora on 2006-11-27
Your icons are all in /home/username/.icons folder... One way you can go find all instances of that icon in those folders and replace it with the one you want. But something tells me that's the really really hard way to do it and there's a better way. ;)  Just in case, here's one option. :)

---

### Post by CatKiller on 2006-11-27
If your theme has neglected to include an icon for the MIME-type you're interested in you can make or assign your own.

The folder you're interested in is either ~/.icons/<*themename*>/<*iconsize*>/mimetypes or /usr/share/icons/<*themename*>/<*iconsize*>/mimetypes, depending on how you installed the theme.

The name you'll need for your icon is gnome-mime-*mimetype* - so for mp3 audio the icon you'd need might be gnome-mime-audio-x-mp3 (I'm not entirely sure what the mimetype is for mp3 at the moment).

Hope this helps.

---

### Post by richardward101 on 2006-11-27
Excellent, that was just the ticket.
Thanks!

IMO this is the sort of thing that should be handled by gconf, but never mind.

---

