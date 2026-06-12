---
title: "Changing colors in gtk 3 theme"
date: 2012-01-09
forum: Art &amp; Design
---

### Post by redman5087 on 2012-01-09
I installed a new gtk 3 theme and I like it very much.
[http://gnome-look.org/content/show.php/SilverImproved?content=146775]("http://gnome-look.org/content/show.php/SilverImproved?content=146775")

But I would like to change some things:

I would like to change the font color of the clock in the panel
I would like to change the textcolor of desktop icons
I would like to change the textcolor of minimized programs in the taskbar.

I'm looking in the gtk.css file but can't find wich option to change.

Can someone with expertise in gtk 3 themes help me?

Thanks

---

### Post by redman5087 on 2012-01-17
Nobody with some knowledge in gtk 3 themes.
Please help

---

### Post by jpfle on 2012-01-18
> **redman5087 said:**
> I would like to change the font color of the clock in the panel

Open the file "gtk-3.0/apps/gnome-panel.css". Find the following code (approximately at the end of the file):

```
ClockBox {
    text-shadow: 0 1 shade (@dark_bg_color, 1.08);
}
```

and add a color property:

```
ClockBox {
    text-shadow: 0 1 shade (@dark_bg_color, 1.08);
    color: @fg_color;
}
```

"@fg_color" refers to a color set in the file "gtk.css". It's the same color used for the menu in the panel. If you want, you can use a custom color, for example (black):

```
ClockBox {
    text-shadow: 0 1 shade (@dark_bg_color, 1.08);
    color: #000000;
}
```

> **redman5087 said:**
> I would like to change the textcolor of desktop icons

Open the file "gtk-3.0/apps/nautilus.css". At the end, add the following:

```
.nautilus-desktop.nautilus-canvas-item {
	color: #ffffff;
	text-shadow: 1 1 alpha (@fg_color, 0.8);
}

.nautilus-desktop.nautilus-canvas-item:active,
.nautilus-desktop.nautilus-canvas-item:prelight,
.nautilus-desktop.nautilus-canvas-item:selected {
	text-shadow: none;
}
```

The font color on the desktop will now be white. Note that the property "text-shadow" is optionnal. You can remove it if you just want to change the color.

> **redman5087 said:**
> I would like to change the textcolor of minimized programs in the taskbar.

In the file "gtk-3.0/apps/gnome-panel.css", add the following at the end:

```
#tasklist-button {
	color: @fg_color;
}
```

---

### Post by redman5087 on 2012-01-19
I feel so stupid that I didn't find this on my own :(

Many thanks for responding :D

---

### Post by johanfa on 2012-03-29
Many thanks to jplfe. These are really very interesting tips.

But I would like to thange the background-color of desktop icons.

My file "gtk-3.0/apps/nautilus.css" contains:

```
.nautilus-desktop.nautilus-canvas-item {
    /*color: @bg_color;*/
    background-image: none;
    background-color: #000000;
    border-radius: 2;
    color: #ffffff;
    /*text-shadow: 1 1 alpha (#000000, 0.8);*/
    text-shadow: none;
}

.nautilus-desktop.nautilus-canvas-item:active {
    background-image: none;
    background-color: alpha (@bg_color, 0.84);
    border-radius: 2;

    color: @fg_color;
}

.nautilus-desktop.nautilus-canvas-item:selected {
    background-image: none;
    background-color: alpha (@selected_bg_color, 0.84);
    border-radius: 2;

    color: @selected_fg_color;
}

.nautilus-desktop.nautilus-canvas-item:active,
.nautilus-desktop.nautilus-canvas-item:prelight,
.nautilus-desktop.nautilus-canvas-item:selected {
    text-shadow: none;
} 
```I can change the color of the text to white, but I can't get a black background when the icon state is normal.

When the icon state is normal, how do you get a background-color?

---

### Post by KEIII on 2012-08-16
Same problem. Still no solution?

---

### Post by Ravi5kumar on 2012-09-04
Me too!

---

### Post by nll on 2012-09-09
Hey, try this: [http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)

---

### Post by France Lipuzic on 2013-07-05
> **johanfa said:**
> I can change the color of the text to white, but I can't get a black background when the icon state is normal.

When the icon state is normal, how do you get a background-color?

I have same problem in 12.04.2 - Still no info about fixing this? Is  there any other wasy to get background color in desktop icons?

---

### Post by redman5087 on 2014-05-05
@jpfle
 
The following code is not working anymore in Ubuntu 14.04 Flashback

I tried to compare with Ambiance and Radiance but I don't find the difference!

```
#tasklist-button {
	color: @fg_color;
}
```

Also I have another problem where there is a semi black line beneath the taskbar, it only appears with the indicators, see screenshot attached.

You're help with be much appreciated...

---

