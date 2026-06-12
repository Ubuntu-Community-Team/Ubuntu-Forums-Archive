---
title: "change font color on panels"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-06-04
how can i change the font color of the clock in the top right, and the applications, places, system menu?

---

### Post by adam.tropics on 2006-06-04
I can't take credit for this but it works for me,

In ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:
```

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

```
and that's it. All you have to do is choose the color and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.

If you want to further want to play with the panel colours, look at the second post down [here,]("http://gnomesupport.org/forums/viewtopic.php?t=10811&postdays=0&postorder=asc&start=0&sid=741762cbe04fda09ac06bc1c69594e6e") it's pretty simple stuff and very handy.

---

### Post by joshrobinson on 2006-06-04
ok thanks for the info :-D ill try it out.. just gota find the color codes for a few till i find the one i like with my wallpaper

---

### Post by TrendyDark on 2006-06-04
[QUOTE=adam.tropics]I can't take credit for this but it works for me,

In ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:
```

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

```
and that's it. All you have to do is choose the color and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.

If you want to further want to play with the panel colours, look at the second post down [here,]("http://gnomesupport.org/forums/viewtopic.php?t=10811&postdays=0&postorder=asc&start=0&sid=741762cbe04fda09ac06bc1c69594e6e") it's pretty simple stuff and very handy.[/QUOTE]

Could you provide a source for this? I'd love to make my panel that has my window-list on it transparent, but it looks ugly.

---

### Post by adam.tropics on 2006-06-04
No worries, the [origonal source]("http://www.ubuntuforums.org/showpost.php?p=494932&postcount=5"), when I asked the exact same question you did!

But to be honest you will do better with the second link above, [again here]("http://gnomesupport.org/forums/viewtopic.php?t=10811&postdays=0&postorder=asc&start=0&sid=741762cbe04fda09ac06bc1c69594e6e"), as it is closer  tied to the gnome development forums.

Advice: Take it or leave it!!

Before you deal with the transpaency, find the colour closest to that of your wallpaper, and using the gnomedev link above as a source, adjust all your colours to be as close as possible to the wallpaper except for obviously the text. Then incrementally adjust the transparency to suit. Total transparency is a nicer idea than practise. Almost totally is much easier to live with! Personal taste i guess.

---

