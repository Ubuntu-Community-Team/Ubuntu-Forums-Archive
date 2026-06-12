---
title: "Everythings Bigger in Ubuntu?"
date: 2009-03-16
forum: Art &amp; Design
---

### Post by Fireblazer on 2009-03-16
Hey,

I noticed that everything seems to be bigger in Ubuntu than in Windows. Like the menus, panels, etc. Is this a screen resolution thing or is that just the way things are?

~ Fireblazer

---

### Post by konqueror7 on 2009-03-16
i don't know by the way you mean big, but you can try tweaking your resolution in ***System > Preferences > Screen Resolution*** or tweak the DPI and font size in the ***System > Preferences > Appearance***...

---

### Post by buldozerceto on 2009-03-16
Also you can lower the font size in system > preferences > appearance, to make things smaller.

---

### Post by JediKnight on 2009-03-16
I have also noticed the same :) Something feels "not right" but I am not sure what though

You could keep some screenshots from each OS and compare them with the next reboot

---

### Post by Fireblazer on 2009-03-17
I'm still workin' on a XP shot but I think it's either DPI or padding, probably padding.
Any way to change that?

~ Fireblazer

---

### Post by alex.rayu on 2009-03-18
In most cases, you can solve the problem by setting the fonts in system > preferences > appearance to 8 pixels.

Yet, some elements, especially in programs like Evolution, like line neight of lists, will not get smaller, because it has images that won't let it get any smaller.

Gnome has historically been criticized for "gigantism". I do believe some of it is true.

---

### Post by ad_267 on 2009-03-18
You could also try using a more compact gtk theme. Have a look at [www.gnome-look.org](www.gnome-look.org). Also see [http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

---

### Post by tuggy on 2009-03-18
Hi,
Yes its true. Mainly its because of GTK.
Check this thread for info and solutions: [http://ubuntuforums.org/showthread.php?t=381133](http://ubuntuforums.org/showthread.php?t=381133)

---

### Post by alex.rayu on 2009-03-18
Again, all hoped for GTK 3

---

### Post by mcduck on 2009-03-18
Wouldn't make any difference. it's not that GTK would have large paddings on GUI widgets, it's that most themes have large paddings. Just use a compact theme and you'll get a compact desktop, no matter if you use GTK3, GTK2, GTK1 or some completely different toolkit.

Anyway, if you need to save screen space there are couple of things you should do:

1. Install some compact GTK2 theme

2. Arrange your panel &other desktop layout to only include only the applets you really need, and then make panels as small as possible. On wide screen displays you should favor panels at sides of the screen as they will use your screen space more efficiently.

2. Set font size to as small as you can read without problems. And set the displays's DPI setting in font options to what fits your resolution & display size.

3. Set the toolbar style to "icons only" in System/Preferences/Appearance/Interface.

4. Set toolbar icon size to small. To do this open gconf-editor, and then change desktop/gnome/interface/toolbar_icon_style to "small-toolbar".

5. Disable menu icons (desktop/gnome/interface/menus_have_icons in gconf-editor). The icons take more vertical space than the text itself does, which results in extra padding around the text.

Of course you should still remember that whitespace is important aspect of usability, and that the difference in screen usage isn't really as big as it seems,  gnome just makes good use of whitespace which makes it look like it's using more screen space than what it actually does. For example people often compare about Gnome's 2-panel layout wasting screen space, when in reality it uses about the same space as KDE's one panel.

---

### Post by FrancoisCN on 2009-03-18
I felt the same way for a while and decided to look for some customization yesterday. It wasn't that hard, but took me a bit of time to find out how to modify some elements of the desktop.

One of the major bug(?) that annoyed me is that the main top panel doesn't go under 24 pixels if you have the applet "Menu Bar" on it (the one with "Applications, Places, System". So I got rid of that and reduced the bar to 20 pixels.

I also changed font sizes in System->Preference->Appearance->Fonts and put everything to 8 pixels.

Another thing that annoyed me was the huge space between the elements in the menus. I fixed that by creating the file ".gtkrc-2.0" in my home folder and adding the following line:

```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-menu=16,16:gtk-large-toolbar=16,16:gtk-button=16,16"
```

Anyways, here's what it looks like now:
[IMG]http://picpost.resolute-guild.com/vigil/screenshot.png[/IMG]

---

### Post by t-mo_ on 2009-03-18
Back to the theme: I still have Vista on my machine (I paid for it. Even if I use it almost never, I do not throw away something I paid for. And since there is no possibility to sell it..) so I can make a comparison. In Vista, really EVERYTHING takes much more space, the screen seems smaller. I didn't change a bit (okay, I build a special conky and changed a few icons) from the original Jaunty alpha 5 installation.

---

