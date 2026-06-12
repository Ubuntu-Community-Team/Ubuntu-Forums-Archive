---
title: "SmoothStreak Application Theme"
date: 2005-06-12
forum: Art &amp; Design
---

### Post by Xian on 2005-06-12
I dont' see this theme mentioned alot so I just wanted to give it a plug as it looks great and has a style which distinguishes itself from many other offerings. Listed below is the link at GnomeArt where you can download it and give it a whirl, and then just a small screenie of a default window using the theme on my Ubuntu box. I edited the gtkrc file to make some color adjustments and I'm using the Bluecurve window border.

[SmoothStreak by Archive](http://art.gnome.org/themes/gtk2/639)


[img]http://img.photobucket.com/albums/v469/camplear/forums/1546.png[/img]

---

### Post by hazza96 on 2005-06-12
I like the look of the icons etc but I am wondering if there is one that uses the Human palette.

I have never customised a theme before, would be easy enough for me to alter the colours of this one? Would anyone want a copy if I did make the same theme using the Human colours?

---

### Post by Xian on 2005-06-12
[QUOTE=hazza96]I have never customised a theme before, would be easy enough for me to alter the colours of this one? Would anyone want a copy if I did make the same theme using the Human colours?[/QUOTE]
I'd certainly like to see such a modification. I'm just a hack at this so I think someone would likely have the palette nailed down better than this example, but it should be fairly close. You'd just substitute it for what is in the default gtkrc.

```
fg[NORMAL]              = "#0f0f0f"
    fg[ACTIVE]              = "#0f0f0f"
    fg[INSENSITIVE]         = "#909090"
    fg[PRELIGHT]            = "#ffffff"
    fg[SELECTED]            = "#ffffff"

    bg[ACTIVE]              = "#d0d0d0"
    bg[NORMAL]              = "#e0e0e0"
    bg[INSENSITIVE]         = "#d2d2d2"
    bg[PRELIGHT]            = "#a26b44"
    bg[SELECTED]            = "#a26b44"

    base[NORMAL]            = "#fdfdfd"
    base[ACTIVE]            = "#a26b44"
    base[INSENSITIVE]       = "#fdfdfd"
    base[PRELIGHT]          = "#ffffff"
    base[SELECTED]          = "#a26b44"

    text[NORMAL]            = "#0f0f0f"
    text[ACTIVE]            = "#ffffff"
    text[PRELIGHT]          = "#ffffff"
    text[SELECTED]          = "#ffffff"
    text[INSENSITIVE]       = "#ffffff"
```

---

### Post by hazza96 on 2005-06-12
I just installed this theme by going:
1. System / Preferences / Theme
2. Clicked the "Install theme" button
3. Browsed to the downloaded tar file.
4. Clciked on "Install"
5. It came up and said that the theme was installed.

The problem is that it isn't on my list, there is no "SmoothStreak" to choose. Have missed a step or is there something else wrong?

---

### Post by Xian on 2005-06-12
I just extracted the theme folder to my /home/<user>/.themes directory (or /usr/share/themes if you prefer) and then selected it from the theme manager by choosing:

Theme Details > Controls > SmoothStreak

Once you do this, and select your preferred icons and window border, you can go back and save the whole theme in the main window of the Gnome Theme Manager under any name you like.

---

### Post by desdinova on 2005-06-15
Very QNX'y - nice

---

