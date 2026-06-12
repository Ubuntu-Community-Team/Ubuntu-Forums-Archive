---
title: "Changing the background image for Gnome notification area?"
date: 2007-04-25
forum: Art &amp; Design
---

### Post by khughitt on 2007-04-25
Heya,

I've searched the web for a while to try and find a way to do this, but have not had any luck. I would like to change the background image of the notification area, to make it stand out more. I know it is possible, but so far i havn't found any documentation on it on the gnome developer's site, or anywhere on google really. 

I tried editing the gtkrc file for the clearlooks theme (at the system level-/usr/share/themes/Clearlooks/gtk-2.0/gtkrc), and added in a class "*Notif* which i had seen someone else use in a forum somewhere, and gave it a style with a obviously different background-color:

```
class "*Notif*"      style "clearlooks-notification"

style "clearlooks-notification" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
  bg[NORMAL] = shade (1.08, @bg_color) # "#66ccff"
}

```

..but after reloading the theme, it did not have any affect :\

Does anyone have any idea how to do this? Any help would be greatly appreciated! Also, somewhat off-topic, but if anyone knows how to modify the background setting for the 'show-desktop' applet so i can give it a transparent background, that would be great too!

Thanks!

---

### Post by kpolice on 2007-04-25
The showdesktop applet is a button, I don't think it's possible to make it completely transparent

---

### Post by khughitt on 2007-04-30
/bump ... anyone ?

---

### Post by kpolice on 2007-04-30
It's not possible because the background from the notification is transparent and actually you see the panel background so the only way is changing the whole panel.

I tried a lot of combinations and neither of them worked.

BTW first you define the style and then you apply it, in your example you first apply it and then define it.

---

### Post by bmroute on 2009-04-24
I'm not sure if the folder structure of my theme is the same as yours, but I went to my theme's folder (which is /home/brandon/.themes/Mac4Lin_MacMenu_V0.4_Beta2), and then to "gtk-2.0/Panel". There was an image called panel-bg.png and I just copied it to "panel-bg 2.png" (for backup) and edited the original one in GIMP. Did "sudo killall gnome-panel" and it worked perfect.

Hope this helps(:

---

