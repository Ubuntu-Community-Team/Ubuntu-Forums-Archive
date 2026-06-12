---
title: "panel volume icons"
date: 2007-04-07
forum: Art &amp; Design
---

### Post by 4KvRMU7Nnv on 2007-04-07
Hi, I was just going through my day customizing my ubuntu when I realized, i don't know how to change the volume control icons in the panel.  I know it is possible but i don't know how.  I am using nouveXT icons if that matters.  Please help!  I would also like to change various icons in the notification area but i don't know how to do that either.

---

### Post by ComplexNumber on 2007-04-07
> **d3br074 said:**
> Hi, I was just going through my day customizing my ubuntu when I realized, i don't know how to change the volume control icons in the panel.  I know it is possible but i don't know how.  I am using nouveXT icons if that matters.  Please help!  I would also like to change various icons in the notification area but i don't know how to do that either.
the volume applet icons that live on the panel are called the following:

audio-volume-high
audio-volume-medium
audio-volume-low
audio-volume-muted

 NOTE: the above names are correct for ubuntu's naming scheme, and they _must_ be named as above for them to show up.


unfortunately, they are named incorrectly in that theme. you will find them in nuoveXT-1.6/32x32/stock/media under the following names:


audio-volume-max
audio-volume-med
audio-volume-min
audio-volume-mute


change them to the names that i've given above, and they will show up. don't bother changing the icons in 24/24 and 16x16.

---

### Post by 4KvRMU7Nnv on 2007-04-07
wow, thanks!  I'll try that right away.  not that it is critical, but does anyone know how to change the notification icons as well?

---

### Post by ComplexNumber on 2007-04-07
> **d3br074 said:**
> wow, thanks!  I'll try that right away.  not that it is critical, but does anyone know how to change the notification icons as well?
it depends what icons that you're referring to that appear in the notification area. again, it depends upon the theme.

---

### Post by 4KvRMU7Nnv on 2007-04-07
ok, I would like to change the battery status icon and the gnome-network-manager icons (they are too colorful for my theme) and I am still using NouveXT icons.

---

### Post by ComplexNumber on 2007-04-07
can you give me a screenshot of what they look like in the notification area  in nuoveXT? i can't find said icons, so it must use the  network manager and battery indicator icons from the icon theme that it inherits - ie  gnome or hicolor.

---

### Post by 4KvRMU7Nnv on 2007-04-07
sure, it's in the attachment.  I'm pretty sure the battery one is inherited from gnome or tango or something like that.  (notification area is top right).

EDIT:  i found the battery it is in /usr/share/icons/hicolor/scalable/apps

I still don't know where the network manager icon is though...

---

### Post by ComplexNumber on 2007-04-07
i forgot about tango. dum-de-dum. 


i think the network-manager isn't an actual icon. if you notice, its dynamic and changes according to if there is a signal and how much. i wouldn't have thought that you could change that, and it probably isn't dependent upon a theme. you could prove my theory wrong, though, by trying out lots of different icon themes and tell me if it changes.

---

### Post by 4KvRMU7Nnv on 2007-04-07
well yes that is true, but i bet it is the same as with the battery icon.  There isn't just one battery icon, there are like 8 different ones to indicate a different level of charge-itude so I am replacing all of them with better ones.  The network manager icons though, i don't think are contained within any of the icon sets that are made becuase it is a separate program.  I bet there is a file somewhere that has them all listed out in some folder, but i just can't find it.

---

### Post by ComplexNumber on 2007-04-07
i had a look in /usr/share/icons and /usr/share/pixmaps, and i couldn't find it.

---

### Post by xopher on 2007-04-08
> 
audio-volume-high
audio-volume-medium
audio-volume-low
audio-volume-muted

I've been wondering about this same thing for a while now too, thanks. :)

Why do the names differ in different themes? Don't we have this 'freedesktop.org icon naming scheme' - or something like that?

---

### Post by ComplexNumber on 2007-04-08
> **xopher said:**
> I've been wondering about this same thing for a while now too, thanks. :)

Why do the names differ in different themes? Don't we have this 'freedesktop.org icon naming scheme' - or something like that?
i guess its because different theme authors write their theme when they're using their own favourite distro. some may use ubuntu, some may use gentoo, some may use fedoras, etc. unfortunately, i don't think there is a common naming scheme except whats been developed for the tango icons. 

also, some theme authors do take other distros into account  by making links in their themes. for example, if they were developing their theme on ubuntu, they would make the audio-volume-high icon, then make a link to the auto-volume-max icon that other distros may use for their naming scheme for that particular icon.

---

### Post by kpolice on 2007-04-09
Network manager icons:
/usr/share/icons/hicolor/22x22/apps

---

### Post by jon_h on 2007-04-11
The volume icons must be in a folder called 'status' and this folder must be referenced in the index.theme file. Also, when I changed the volume icons in my icon theme to be more like OSX, I had to make small versions, as 128x128 pngs didn't work. And because they were small, I had to create a whole new folder, and refernce that in index.theme at the right size.

---

### Post by ComplexNumber on 2007-04-11
> The volume icons must be in a folder called 'status'it doesn't have to be. the icon ttheme arthor could put them all in 1 directory and the theme would still work, provided that the index.theme file was changed accordingly. the classification of icons into their respective folders such as apps, actions, emblems, categories, stock, etc is for clarity purposes. putting them all in 1 folder may well cause problems for themes that inherit that theme, possibly.

---

