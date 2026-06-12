---
title: "How to make theme have transparent toolbars etc?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by toxicgtr on 2007-10-27
Hey,

Have just installed the moomex-theme, how do i get the toolbars transparent like in the pictures etc. I'm running Gusty. [http://www.gnome-look.org/content/show.php/moomex-theme?content=57063]("http://www.gnome-look.org/content/show.php/moomex-theme?content=57063")

---

### Post by toxicgtr on 2007-10-27
Bump.

---

### Post by Niniel on 2007-10-27
Not sure if this is what you want, but you can right-click on the panel/s, go to Properties, then to the Background tab, and there click on Solid Colour, which activates transparency.

---

### Post by multifaceted on 2007-10-27
Like Niniel said: Right click the panel to properties>background>solid color -transparency

If you want the polished "glassy" look shown in your link the, just download the theme and use it!:)

---

### Post by toxicgtr on 2007-10-27
Well ive installed the theme, this is what it looks like: [http://upload.goome.co.nz/data/76a63fdf4bScreenshot.png](http://upload.goome.co.nz/data/76a63fdf4bScreenshot.png) but i want it to look like the one pictured here: [http://www.gnome-look.org/content/show.php/moomex-theme?content=57063&PHPSESSID=bfb042e3dece9f0bce7d3176ee1f10c9](http://www.gnome-look.org/content/show.php/moomex-theme?content=57063&PHPSESSID=bfb042e3dece9f0bce7d3176ee1f10c9)

---

### Post by avik on 2007-10-27
Also note that the theme in question is not the only thing responsible for the transperancies.  The reference pictures show a system running Compiz-Fusion with the Reflection plug-in.

---

### Post by toxicgtr on 2007-10-27
Do you know what settings to use etc to get it like the picture tho?

---

### Post by avik on 2007-10-27
> Do you know what settings to use etc to get it like the picture tho?

Do you have Compiz-Fusion running?  You'll need it.

Enable Reflections and Window Previews.

---

### Post by slightlybartfast on 2008-04-16
EDIT I didn't look at the last post date :S     Oh well lol

The way to make the windows and toolbars transparent is to:

1. Make sure you have compiz manager installed (CompizConfig).
2.Goto the General Options.
3. then the Opacity Settings tab.
4. the  add the following to opacity windows:

```

 (name=Vista) | (name=gimmie_applet) | (name=gnome-panel) | (type=Menu | PopupMenu | DropdownMenu | toolbar | utility | combo | input | Normal)

```

adjust the opacity to how you want it.
Theres a list of different window types on the compiz website.


The next part allows you to blur the transparency if you want.
 
5.Go back to the main Comizconfig catagory page.
6.Check and then click on Blur windows
7. Make sure alpha blur windows is checked
8.Paste the following into the "Alpha blur windows" edit box:

```

 (name=Vista) | (name=gimmie_applet) | (name=gnome-panel) | (type=Menu | PopupMenu | DropdownMenu | toolbar | utility | combo | input | Normal)

```

This is the same as the last code.
I personally prefer the Gaussian blur type, however mess around.

I got this info from another web site, I didn't figure it out myself, I just can't remember where I found it.

If someone knows how to get it to blur toolbars, and not the main work areas then that'd be great. as I like to watch video's on a solid background and work on a solid back ground, however like the idea of glass toolbars.

I couldn't get 

```

(type=toolbar) | (!type=fullscreen) 

```
 to work....anyone have any ideas?

Cheers

---

