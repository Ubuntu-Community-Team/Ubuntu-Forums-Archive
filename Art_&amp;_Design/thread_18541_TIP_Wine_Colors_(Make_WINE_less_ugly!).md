---
title: "TIP: Wine Colors (Make WINE less ugly!)"
date: 2005-03-07
forum: Art &amp; Design
---

### Post by Chibi on 2005-03-07
Ever gotten annoyed by Wine/Cedega/CXOffice not matching to your otherwise uberpretty desktop? Well, this isn't quite a perfect solution, but I highly doubt WINE is ever going to get a GTK theme overlay system of any sort, so give this a shot--

Open 
~/.wine/user.reg
or
~/.transgaming/user.reg
and look for [Control Panel\\Colors], It /should/ be the first registry entry. Now that you've got that found, replace it with the following chunk

```

[Control Panel\\Colors] 1105779303
"ActiveBorder"="226 226 226"
"ActiveTitle"="226 226 226"
"AppWorkSpace"="198 198 191"
"Background"="93 77 52"
"ButtonAlternativeFace"="200 0 0"
"ButtonDkShadow"="85 85 82"
"ButtonFace"="226 226 226"
"ButtonHilight"="255 255 255"
"ButtonLight"="255 255 255"
"ButtonShadow"="198 198 191"
"ButtonText"="0 0 0"
"GradientActiveTitle"="226 226 226"
"GradientInactiveTitle"="226 226 226"
"GrayText"="198 198 191"
"Hilight"="179 145 105"
"HilightText"="0 0 0"
"InactiveBorder"="226 226 226"
"InactiveTitle"="226 226 226"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="200 0 0"
"Menu"="226 226 226"
"MenuBar"="0 0 0"
"MenuHilight"="179 145 105"
"MenuText"="0 0 0"
"Scrollbar"="226 226 226"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"

```

That will theme your WINE to ClearLooks-Ubuntu color-wise (Which is the most comfortable theme ever, in my opinion.)

If you don't want it themed to clearlooks, this should be an easy enough template to go about figuring things. If you need a reference to what themes what UI element.. Uhhh... Try looking around some windows site, or just wing it like I did ^_^

I hope this tip makes your Ubuntu a more bootiful and happy place.
Comments? Theme configurations to match your favorite GTK theme? Post them here.

---

### Post by landotter on 2005-03-07
here's what it looks like for the curious:

[img]http://photos3.flickr.com/6082887_c84f21eb17.jpg[/img]

---

### Post by Chibi on 2005-03-07
Heh. Again, it's supposed to go with Clearlooks-Ubuntu, not Industrial-Human, so the colors are a little off the normal ubuntu scheme.

You can check the giant clearlooks thread for clearlooks, Clearlooks-Ubuntu is in one of the theme packs. (And I highly recommend it, it's easier on the eyes, fits well with the rest of Ubuntu, and goes great with the Human icon set.) :D

I'll put up an Industrial-Human colorscheme later if no one else does before I wake up. z_Z.. Nighty.

---

### Post by landotter on 2005-03-07
[QUOTE=Chibi]Heh. Again, it's supposed to go with Clearlooks-Ubuntu, not Industrial-Human, so the colors are a little off the normal ubuntu scheme[/QUOTE]

I deleted Clearlooks human since I really don't like the Human colour scheme--just changed it for the screenie, so it would be in the ballpark. :P I don't mind the brown and green at all, just wish the application "bodies" had a warmer shade. That's why I'm a Clearlooks olive user. ;)

Funny though, since Gimp 2.x came out, I really don't use Photoshop anymore, as I much prefer the Gimp's ui.

---

### Post by Jad on 2005-03-07
Thank you for the TIP!
works smoothly now

---

### Post by KillerKiwi on 2006-11-27
```

[Control Panel\\Colors] 1105779303
"ActiveBorder"="239 235 231"
"ActiveTitle"="239 235 231"
"AppWorkSpace"="198 198 191"
"Background"="93 77 52"
"ButtonAlternativeFace"="200 0 0"
"ButtonDkShadow"="85 85 82"
"ButtonFace"="239 235 231"
"ButtonHilight"="255 255 255"
"ButtonLight"="255 255 255"
"ButtonShadow"="198 198 191"
"ButtonText"="0 0 0"
"GradientActiveTitle"="239 235 231"
"GradientInactiveTitle"="239 235 231"
"GrayText"="198 198 191"
"Hilight"="179 145 105"
"HilightText"="0 0 0"
"InactiveBorder"="239 235 231"
"InactiveTitle"="239 235 231"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="200 0 0"
"Menu"="239 235 231"
"MenuBar"="0 0 0"
"MenuHilight"="179 145 105"
"MenuText"="0 0 0"
"Scrollbar"="239 235 231"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"

```

This is closer to the edgy theme

---

### Post by xiaoxin on 2006-12-31
```
"ActiveBorder"="239 235 231"
"ActiveTitle"="239 235 231"
"AppWorkSpace"="198 198 191"
"Background"="93 77 52"
"ButtonAlternativeFace"="200 0 0"
"ButtonDkShadow"="85 85 82"
"ButtonFace"="239 235 231"
"ButtonHilight"="255 255 255"
"ButtonLight"="255 255 255"
"ButtonShadow"="198 198 191"
"ButtonText"="0 0 0"
"GradientActiveTitle"="239 235 231"
"GradientInactiveTitle"="239 235 231"
"GrayText"="198 198 191"
"Hilight"="247 203 135"
"HilightText"="0 0 0"
"InactiveBorder"="239 235 231"
"InactiveTitle"="239 235 231"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="200 0 0"
"Menu"="239 235 231"
"MenuBar"="0 0 0"
"MenuHilight"="247 203 135"
"MenuText"="0 0 0"
"Scrollbar"="239 235 231"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"
```

Even closer 8)

---

### Post by hikaricore on 2006-12-31
> **xiaoxin said:**
> ```
"ActiveBorder"="239 235 231"
"ActiveTitle"="239 235 231"
"AppWorkSpace"="198 198 191"
"Background"="93 77 52"
"ButtonAlternativeFace"="200 0 0"
"ButtonDkShadow"="85 85 82"
"ButtonFace"="239 235 231"
"ButtonHilight"="255 255 255"
"ButtonLight"="255 255 255"
"ButtonShadow"="198 198 191"
"ButtonText"="0 0 0"
"GradientActiveTitle"="239 235 231"
"GradientInactiveTitle"="239 235 231"
"GrayText"="198 198 191"
"Hilight"="247 203 135"
"HilightText"="0 0 0"
"InactiveBorder"="239 235 231"
"InactiveTitle"="239 235 231"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="200 0 0"
"Menu"="239 235 231"
"MenuBar"="0 0 0"
"MenuHilight"="247 203 135"
"MenuText"="0 0 0"
"Scrollbar"="239 235 231"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"
```

Even closer 8)

Damn nice :)  Thanks.

---

### Post by Yellow Onion on 2007-07-13
"InfoWindow"="200 0 0"

looks extremly red I deleted the entry and it matches perfectly with the feisty theme because the default is same

---

### Post by Endolith on 2009-02-02
I wrote a script to scrape the colors from GTK and apply them to Wine, so it matches no matter what your colors or theme.  It's not perfect, but it works pretty well with the usual engines.

[http://www.endolith.com/wordpress/2008/08/03/wine-colors/](http://www.endolith.com/wordpress/2008/08/03/wine-colors/)

---

### Post by Crafty Kisses on 2009-02-02
> **Endolith said:**
> I wrote a script to scrape the colors from GTK and apply them to Wine, so it matches no matter what your colors or theme.  It's not perfect, but it works pretty well with the usual engines.

[http://www.endolith.com/wordpress/2008/08/03/wine-colors/](http://www.endolith.com/wordpress/2008/08/03/wine-colors/)

Thanks, I'm going to try that out. :)

---

### Post by alex.rayu on 2009-02-03
Awesome.

---

### Post by morgengenuss on 2009-02-03
tried it on (x)ubuntu 8.10 with various gtk-themes/engines (clearlooks, murrine, aurora), always get the following error output:
```
Traceback (most recent call last):
  File "wine_colors_from_gnome.py", line 127, in <module>
    color_pairs.append('"Background"="%s"' % format_hex_color(desktop_color))
  File "wine_colors_from_gnome.py", line 28, in format_hex_color
    return "%s %s %s" % (int(r,16), int(g,16), int(b,16))
ValueError: invalid literal for int() with base 16: ''
```
(i apologize for this indecent place for a bug-report.)


otherwise: two thumbs up for the project!

---

### Post by Endolith on 2009-02-03
> **morgengenuss said:**
> tried it on (x)ubuntu 8.10 with various gtk-themes/engines (clearlooks, murrine, aurora), always get the following error output:
```
Traceback (most recent call last):
  File "wine_colors_from_gnome.py", line 127, in <module>
    color_pairs.append('"Background"="%s"' % format_hex_color(desktop_color))
  File "wine_colors_from_gnome.py", line 28, in format_hex_color
    return "%s %s %s" % (int(r,16), int(g,16), int(b,16))
ValueError: invalid literal for int() with base 16: ''
```(i apologize for this indecent place for a bug-report.)


otherwise: two thumbs up for the project!

Thanks for testing this.  I'm not surprised that it doesn't work in Xubuntu, really, but can you test something?  Just add this print line to the function and tell me what it says when you run the script:

[php]def format_hex_color(color):
    """ Convert from #rrrrggggbbbb string to decimal "RRR GGG BBB" triple. """
    r, g, b = color[1:3], color[5:7], color[9:11]
    print('Bad color: ' + color)
    return "%s %s %s" % (int(r,16), int(g,16), int(b,16))[/php]

---

### Post by morgengenuss on 2009-02-05
done. the "bad" color seems to be dark brownish:
```
Bad color: #4E3E29
```

and (without having had a real look into the code): why exactly are you surprised it doesn't work in xubuntu?

---

### Post by Endolith on 2009-02-05
> **morgengenuss said:**
> done. the "bad" color seems to be dark brownish:
```
Bad color: #4E3E29
```

A dark brownish, like the default Ubuntu desktop color? ;)

On my computer, it returns a color in the form #rrrrggggbbbb, but the default Ubuntu color is apparently in the form #RRGGBB.  

It's easy enough to make it recognize both, but I doubt the color in GNOME's configuration actually matches your Xfce desktop color anyway.  Does it?  I don't know how to extract the desktop color for Xfce.

> and (without having had a real look into the code): why exactly are you surprised it doesn't work in xubuntu?I am *not* surprised that it doesn't work in Xubuntu, since I didn't design it for Xubuntu or test it in Xubuntu.  :)  But if the desktop color is the only issue, I can make it just skip that when it doesn't work and it will at least match the rest of the GTK theme.  Just change that function to this for now, and the rest of the script should work:

[php]def format_hex_color(color):
    return '0 0 0'[/php]

---

### Post by morgengenuss on 2009-02-06
yep, that worked.
> It's easy enough to make it recognize both, but I doubt the color in GNOME's configuration actually matches your Xfce desktop color anyway. Does it? I don't know how to extract the desktop color for Xfce.
well, what exactly is the "desktop color" you're referring to?

---

### Post by Endolith on 2009-02-06
> **morgengenuss said:**
> yep, that worked.

All the other colors were read correctly?

> well, what exactly is the "desktop color" you're referring to?The solid desktop color "behind" the wallpaper:

[http://www.techotopia.com/images/0/02/Ubuntu_change_desktop_background.jpg](http://www.techotopia.com/images/0/02/Ubuntu_change_desktop_background.jpg)

I don't know anything about Xfce.  Maybe it doesn't even have a Desktop color.  :)

Edit: Maybe you meant "what's the desktop color in Wine"?  It only appears if you choose "virtual desktop" in wineconfig, for programs that don't play well without it.

---

### Post by morgengenuss on 2009-02-07
> All the other colors were read correctly?
yep, i would say so. at least as far as i can see now.

> The solid desktop color "behind" the wallpaper:
i see, yes xfce does have something like that. you find it in /home/$USER/.config/xfce4/mcs_settings/desktop.xml

the two lines (you can actually choose to have a gradient between two colors as a background) are:
```
<option name="color1_0_0" type="color" value="28195,0,0,65535"/>
<option name="color2_0_0" type="color" value="15872,26624,40448,65535"/>
```
(the first line is the one you're looking for if you're talking about the "solid" setting.)

the value "28195" equals #6E0000 in hexadecimal. (don't ask me what kind of format this color value is...)


edit: anyways, i don't think the desktop color is that important... (i rarely see any application using the virtual desktop)

---

### Post by Endolith on 2009-02-07
> **morgengenuss said:**
> yep, i would say so. at least as far as i can see now.


great!

> i see, yes xfce does have something like that. you find it in /home/$USER/.config/xfce4/mcs_settings/desktop.xml

Thanks, I'll add it to the script.

> value="28195,0,0,65535"

the value "28195" equals #6E0000 in hexadecimal. (don't ask me what kind of format this color value is...)

Divide each number by 256 and convert to hex.

>  anyways, i don't think the desktop color is that important... (i rarely see any application using the virtual desktop)

Yeah, it's only used if the user tells it to.  I have a program that tries to draw a weird bar at the bottom of the screen outside of any windows, and if I don't use virtual desktop it screws up a lot.

---

### Post by morgengenuss on 2009-02-09
good stuff, anyways thanks for writing the script, i really think it's a great idea and long overdue!
(and as far as xfce-compatibility goes, i'm quite confident now that it works; tested it several times.)

i think this script (or at least the functionality) should be integrated in wine.

---

### Post by Endolith on 2009-02-10
> **morgengenuss said:**
> i think this script (or at least the functionality) should be integrated in wine.

I do, too.  It certainly isn't ready yet, though.  I wish I could get more help with it, but I don't know who to ask.  It needs to be modified to work with every theme, needs to be called automatically when the theme is changed, needs to incorporate fonts as well as colors, etc.

It's supposedly [going to be added to Wine Doors]("http://www.wine-doors.org/trac/ticket/411").

---

### Post by morgengenuss on 2009-02-13
i fear i don't know enough about gtk-engines to be of any help here.

well, it should be rather easy to retrieve the system font from xfce, you'll find it in /home/$USER/.config/xfce4/mcs_settings/gtk.xml, line 8:
```
<option name="Gtk/FontName" type="string" value="Sans 9"/>
```
(note: this is true for xfce 4.4.*, afaik this will change in xfce 4.6 which should be included in jaunty. but i can keep you updated on that.)

> needs to be called automatically when the theme is changed
not so sure, whether that's really such a good idea (that would mean it would be incorporated in the standard gtk-theme-switcher of gnome respectively xfce). i would just add it to the wine-settings dialogue.
tbh i don't switch themes so often, so i don't think it's such an annoyance.

---

### Post by Endolith on 2009-02-16
> **morgengenuss said:**
> well, it should be rather easy to retrieve the system font from xfce, you'll find it in /home/$USER/.config/xfce4/mcs_settings/gtk.xml, line 8:
```
<option name="Gtk/FontName" type="string" value="Sans 9"/>
```(note: this is true for xfce 4.4.*, afaik this will change in xfce 4.6 which should be included in jaunty. but i can keep you updated on that.)

There is an xfce4 module for Python.  I wonder if these things could be accessed through that instead of relying on files that might change?

---

### Post by morgengenuss on 2009-02-17
> There is an xfce4 module for Python. I wonder if these things could be accessed through that instead of relying on files that might change?
possibly. but the thing is that since the whole framework is going to change from mcs_settings to xfconf the python bindings will be affected by this too. furthermore if i was you i wouldn't want to make the python bindings for xfce 4.* a dependency for your script...

(btw i just looked up the website of those [python bindings]("http://pyxfce.xfce.org/"), at the moment they seem to work for xfce 4.4.* only and there's no sign of further development.)

---

