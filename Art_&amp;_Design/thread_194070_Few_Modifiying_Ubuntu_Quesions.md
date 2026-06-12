---
title: "Few Modifiying Ubuntu Quesions"
date: 2006-06-10
forum: Art &amp; Design
---

### Post by arottenmind on 2006-06-10
I have a few questions about modifiying Ubuntu

Is there a way to change Font color from black to white for the words in the windows list on the panel, and the font color for say things like the weather report that is on the panel

Is there a good Black Panel background, currently have a makshift one that looks bad (not a graphics artist)

The selected windows in the windows list still display as white backgrounds, can this be edited?

The little dots on the left side of the windows list, and the system notifiyer, are the able to be removed?

Last one, how do you change the splash screen that happens after you login in

Thanks! :D

---

### Post by Lux Perpetua on 2006-06-11
The font color can be changed by modifying the gtkrc file of your theme; I don't know of another way (which doesn't mean there isn't one). 

This would be at ~/.themes/*name-of-theme*/gtk-2.0/gtkrc

If the theme you're using isn't in ~/.themes, then it is probably in /usr/share/themes, in which case you should copy it over to your .themes directory (create it if you have to) before playing with it. 

I haven't done this in a while, but it is not difficult to hack gtkrc files to change colors. You'll see lines like 

base[NORMAL] = "#ffffff"

This sets some color to white (red = ff, green = ff, blue = ff). It's been a while, so I can't tell you exactly which ones you need to change, but you can use a process of elimination. #ffffff is white, and #000000 is black. As you make changes, you can see how they look by reselecting your theme in the theme manager. 

As for the panel background: I think you can also change that in the gtkrc (but I'm rusty). I do recall that sometimes I had to execute a killall gnome-panel for my changes to show up. 

I don't know about the windows list; I don't seem to have it. 

For the splash screen: System->Administration->Login Window can help, although it seems fairly rudimentary.

---

### Post by arottenmind on 2006-06-11
Thanks alot Lux, all that worked for me :D

---

### Post by Who on 2006-06-25
[QUOTE=arottenmind]Thanks alot Lux, all that worked for me :D[/QUOTE]

Which 'class' did you apply the changes to so that it would affect only the panel window list?

---

### Post by bvc on 2006-06-25
I just put this in ~/.gtkrc-2.0 (create it if not there)
```
style "panel"
{
  fg[NORMAL]					= "#F9FBF6"
# fg[PRELIGHT]					= "#222222"
#  fg[ACTIVE]					= "#ffffff"
#  fg[SELECTED]				= "#000000"
#  fg[INSENSITIVE]				= "#8A857C"

#  bg[NORMAL]					= "#000000"
#  bg[PRELIGHT]				= "#dfdfdf"
#  bg[ACTIVE]					= "#D0D0D0"
#  bg[SELECTED]				= "#D8BB75"
#  bg[INSENSITIVE]				= "#EFEFEF"

# base[NORMAL]				= "#ffffff"
#  base[PRELIGHT]				= "#EFEFEF"
#  base[ACTIVE]				= "#D0D0D0"
#  base[SELECTED]				= "#DAB566"
#  base[INSENSITIVE]			= "#E8E8E8"

#  text[NORMAL]				= "#161616"
#  text[PRELIGHT]				= "#000000"
#  text[ACTIVE]					= "#000000"
#  text[SELECTED]				= "#ffffff"
#  text[INSENSITIVE]				= "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"
```

That controlling [this]("http://gnomethemes.org/pre/nm156-2-full.jpg")

---

