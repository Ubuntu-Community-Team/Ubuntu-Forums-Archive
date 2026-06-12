---
title: "[SOLVED] change gtk-2 themes setting"
date: 2008-04-07
forum: Art &amp; Design
---

### Post by tommyhakinen on 2008-04-07
hi,

I am having a little problem with gtk-2 theme. I just installed the elegance theme from gnome-look. When I increase the panel size beyond 30, the panel image seems to be repeating. how do i get rid of this repetition? i want to have bigger panel to show the icons.

thank you.

best regards,

tommy

---

### Post by fela on 2008-04-07
add a custom background image: right click panel, properties, background.

---

### Post by smartboyathome on 2008-04-07
You have to make a background image which is bigger. It doesn't "stretch" the image due to it being a pixmap.

---

### Post by mcduck on 2008-04-08
> **smartboyathome said:**
> You have to make a background image which is bigger. It doesn't "stretch" the image due to it being a pixmap.
Actually stretching and rotating of panel images can be enabled through gconf-editor. But it only works for images you have set as panel background through panel's configuration menu, not for panel backgrounds included in the GTK theme.

Because of this it's best to comment out the panel background line from the theme's gtkrc-file, and then add the image yourself to the panel.

The gconf settings are in apps/panel/toplevels/<NAME-OF-YOUR-PANEL>/background, just enable "stretch" (or "fit" to respect aspect of the original image, although that one puts some restrictions on possible panel/image sizes). You can also enable "rotate" if you use vertical panels.

---

### Post by tommyhakinen on 2008-04-08
thanks. it works.

---

### Post by FuturePilot on 2008-04-09
> **mcduck said:**
> Actually stretching and rotating of panel images can be enabled through gconf-editor. But it only works for images you have set as panel background through panel's configuration menu, not for panel backgrounds included in the GTK theme.

Because of this it's best to comment out the panel background line from the theme's gtkrc-file, and then add the image yourself to the panel.

The gconf settings are in apps/panel/toplevels/<NAME-OF-YOUR-PANEL>/background, just enable "stretch" (or "fit" to respect aspect of the original image, although that one puts some restrictions on possible panel/image sizes). You can also enable "rotate" if you use vertical panels.
Wow, I had no clue about that settings in Gconf. All this time I've been resizing images to fit the panel....

---

