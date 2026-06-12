---
title: "gnome icon theme index incorrect"
date: 2007-06-29
forum: Art &amp; Design
---

### Post by tao1 on 2007-06-29
Hi,

IMO gnome icon theme index is incorrect (/usr/share/icons/gnome/index.theme).
Because the 48x48/apps section is of type Scalable, I think it should be Fixed, or it should contain MinSize and MaxSize.

Regards,

Laurent.

---

### Post by ComplexNumber on 2007-06-29
on mine it says "Fixed" for all of them except Applications. i don't know why, but it should be "Fixed". here is the section in question:

```
[48x48/actions]
Size=48
Context=Actions
Type=Fixed

[48x48/animations]
Size=48
Context=Animations
Type=Fixed

[48x48/apps]
Size=48
Context=Applications
Type=Scalable

[48x48/categories]
Size=48
Context=Categories
Type=Fixed

[48x48/devices]
Size=48
Context=Devices
Type=Fixed

[48x48/emblems]
Size=48
Context=Emblems
Type=Fixed

[48x48/filesystems]
Size=48
Context=FileSystems
Type=Fixed

[48x48/mimetypes]
Size=48
Context=MimeTypes
Type=Fixed

[48x48/places]
Size=48
Context=Places
Type=Fixed

[48x48/stock/code]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/document]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/generic]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/io]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/net]
Size=48
Context=Stock
Type=Fixed
```

---

### Post by Crafty Kisses on 2007-06-29
> **ComplexNumber said:**
> on mine it says "Fixed" for all of them except Applications. i don't know why, but it should be "Fixed". here is the section in question:

```
[48x48/actions]
Size=48
Context=Actions
Type=Fixed

[48x48/animations]
Size=48
Context=Animations
Type=Fixed

[48x48/apps]
Size=48
Context=Applications
Type=Scalable

[48x48/categories]
Size=48
Context=Categories
Type=Fixed

[48x48/devices]
Size=48
Context=Devices
Type=Fixed

[48x48/emblems]
Size=48
Context=Emblems
Type=Fixed

[48x48/filesystems]
Size=48
Context=FileSystems
Type=Fixed

[48x48/mimetypes]
Size=48
Context=MimeTypes
Type=Fixed

[48x48/places]
Size=48
Context=Places
Type=Fixed

[48x48/stock/code]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/document]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/generic]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/io]
Size=48
Context=Stock
Type=Fixed

[48x48/stock/net]
Size=48
Context=Stock
Type=Fixed
```

Thanks!

---

### Post by bvc on 2007-06-30
why should it be fixed?

---

### Post by ComplexNumber on 2007-07-01
> **bvc said:**
> why should it be fixed?
because they are not intended to be scalable and they are 48x48 png(the same as the other categories in the 48x48 directory).

---

### Post by bvc on 2007-07-01
but who says they are not intended to be scalable? BTW, my filesystems and mimetypes are also scalable in my index file. Don't confuse svg with the option to have a png scaled to a smaller size. They are maxed at 48 so, nothing at all is hurt by putting Scalable. Infact, I often have to fix bad icon themes this way. I'd rather have the icon show up were needed scaled down than have the gnome icon show up because they put fixed instead of Scalable. Fixed is only useful if you have all the diff icons and all the diff sizes, which has been what, one theme in the history of gnome? If even one.

---

### Post by ComplexNumber on 2007-07-01
take a few random icons from each of the categories  in the 48x48 directory as i had done earlier, then scale them up. they are all as 'scalable' as each other. so either the apps entry is wrong, or all the other are wrong and that one is correct.
that's how it seems to me.

---

### Post by bvc on 2007-07-01
that's the point. It's not done for scaling up but down.
I haven't dug all through it to see if that's why for the gnome icon theme, but I know that's why in themes in general. That's all I am saying. Scalable does not = svg

---

### Post by ComplexNumber on 2007-07-01
to my mind, that doesn't sound right because if they are all the same, then they would either all be scalable or all fixed. i also know that if, for example, the panel is of size 22, it will use the next set up in size(ie 24x24) for the icons. meaning, it is scaled down.

---

