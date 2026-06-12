---
title: "Make panel invisible"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-12-10
Alright so the one thing to make my desktop look completely awesome (or at least the way I like it), I need to make the panels I have invisible, so only the icons and buttons on it are showing. If I can't have it completely invisible, I at least want to make the little dotted grabbers as transparent as possible. How can I do this? I tried setting the background of the panel to a transparent image but that didn't work.

---

### Post by -grubby on 2007-12-10
right click on panel>properties>tab to background> set to "solid color" and adjust the bar under it to the required transparency

---

### Post by mikewhatever on 2007-12-10
You can make the panels transparent by right clicking, properties, background tab.

---

### Post by akiratheoni on 2007-12-10
Sorry for not being specific enough. I've done that, but I also want to get rid of the little grabber handles that you use to drag around the panel.

EDIT: I attached a pic so you guys can understand. I want to make invisible the things I circled.

Also, is it possible to make the outline of the panel invisible? So there's absolutely nothing there but the icons?

---

### Post by mikewhatever on 2007-12-10
In the General tab uncheck Show hide buttons.

---

### Post by akiratheoni on 2007-12-10
Hm it's unchecked... not exactly what I wanted, but thanks for the help. Sorry.

---

### Post by mikewhatever on 2007-12-10
> **akiratheoni said:**
> Hm it's unchecked... not exactly what I wanted, but thanks for the help. Sorry.

Expand the panel by checking the first option in the General tab, that should hide the arrows. You can then move things around on the panel to get them to the right position.

---

### Post by zero-9376 on 2007-12-10
these are not hide panel arrows but handles for  the different sections of the panel, specifically the window list and notification area

[http://ubuntuforums.org/showthread.php?t=358961](http://ubuntuforums.org/showthread.php?t=358961)

EDIT: just to clarify - as the thread above says you cannot hide these using any panel setting the only thing you can do is use a different theme or change the theme

---

### Post by ncappel1 on 2007-12-11
What those dotted boxes are for is to grab the panel and drag it around when it is not expanded. if the panel is expanded in properties->general, the dotted lines will go away. 

then you can set 100% transparency, and set your icons manually to the center of the now invisible panel.

edit: if you want to experiment with some different panels, look at the AWN windowmanager or Kiba-dock each one is cool in their own respects, but both lack functionality that is very useful in the default panel (the network manager applet (nm-applet) for example.

---

### Post by akiratheoni on 2007-12-11
> **ncappel1 said:**
> What those dotted boxes are for is to grab the panel and drag it around when it is not expanded. if the panel is expanded in properties->general, the dotted lines will go away. 

then you can set 100% transparency, and set your icons manually to the center of the now invisible panel.

edit: if you want to experiment with some different panels, look at the AWN windowmanager or Kiba-dock each one is cool in their own respects, but both lack functionality that is very useful in the default panel (the network manager applet (nm-applet) for example.

Yeah, I'm using AWN. The reason why I want to get the panel docks to go away is because currently my desktop is looking like this:

[http://img102.imageshack.us/img102/3406/image5yc5.png](http://img102.imageshack.us/img102/3406/image5yc5.png)

See? If I were to make the icons and USP menu that I have look like it's not on a panel and instead on the wallpaper itself, it would make my desktop look really cool and I'd love Ubuntu forever (not that I didn't before, though :P)

---

### Post by nikoPSK on 2007-12-11
goto compiz, general options, opacity settings. Add "dock" and set the transparency to whatever level you want. To make matching menus do "dropdownmenu" if you have the other form of menu that goes up do "popupmenu".

Enjoy.

---

### Post by mcduck on 2007-12-11
It's not possible to get rid of the handles at the ends of non-expanded gnome panel, at least without modifying the source code of the panel.

But there is a simple trick that you can use to get rid of the handles for Window List and Notification Area applets:

1. Open Gimp and create empty, transparent image with size of 1x1 pixels. Save it as ".pixel.png" in your home directory (The dot in the beginning of the filename makes it hidden file so you won't see it in your home).  Or use the one I've made and just extract it from the attached .zip into your home.

2. Open text editor, paste the following code in it and save the file as ".gtkrc-2.0" inside your home directory.

```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function = HANDLE
      file = ".pixel.png"
      border = { 0, 0, 0, 0 }
      stretch = TRUE
      orientation = VERTICAL
    }
    image
    {
      function = HANDLE
      file = ".pixel.png"
      border = { 0, 0, 0, 0 }
      stretch = TRUE
      orientation = HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

3. Log out and back again.

This will replace the panel handle images with the empty, transparent image you created, making the handles invisible.

---

### Post by akiratheoni on 2007-12-11
Thanks for the reply. I'll try it when I get home :)

---

