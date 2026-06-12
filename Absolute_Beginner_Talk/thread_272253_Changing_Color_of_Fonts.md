---
title: "Changing Color of Fonts"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Eddie Wilson on 2006-10-05
Hello All,
How do you change the color of the fonts in Gnome.
Thanks,
Iguana

---

### Post by chavo on 2006-10-05
This is most easily accomplished by changing the theme. GTK is very customizable but there is no easy GUI way to change colors of individual elements like in KDE or Windows. The way GTK is written you can change colors or themes for individual widgets in individual apps if you wanted to. 

The easiest way to change just the colors of the fonts would be to create a ~/.gtkrc-2.0 file and paste this in there ->
```

style "font_color"
{
  fg[NORMAL]        = "#3b3b3b"
}

class "GtkWidget" style "default"

```

Then just change the #3b3b3b to the color of your choice. Now keep in mind this will still be in effect when you change themes as it over rides the one set in the theme, so you'll have to delete or edit the file if you change themes later on.

You can also edit the gtkrc file for the theme directly. If you installed the theme it's in ~/.themes and a system installed theme lies in /usr/share/themes, copy it to ~/.themes first.

Like I said GTK is very flexible in it's theming, there's just no easy way to change things.

---

