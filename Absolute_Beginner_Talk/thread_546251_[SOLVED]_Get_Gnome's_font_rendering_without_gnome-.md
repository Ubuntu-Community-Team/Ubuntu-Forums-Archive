---
title: "[SOLVED] Get Gnome's font rendering without gnome-settings-daemon"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by jordanmthomas on 2007-09-08
I've got gnome set up to render fonts exactly as I want them.  The problem is, I don't use gnome any more.  Now, I usually just use a .gtkrc-whatever.  This works great for the most part.  My theme is right, my icons are right, my font is the correct font.

The only problem is it doesn't seem to have the same rendering options as when gnome is running.  I can get the correct rendering if I run gnome-settings-daemon when I run my normal window manager.  I'd rather not run gnome-settings-daemon though since it really shouldn't be necessary and with it even dwm gets a little heavy on RAM usage.

.xinitrc
```
xmodmap ~/.Xmodmap
xbindkeys
xcompmgr -Cc &
gnome-volume-manager &
gnome-settings-daemon &  #want this GONE
eval `cat $HOME/.fehbg`
exec dwm-launch
```

I've done some homework, and I am pretty sure I need to edit my .fonts.conf.  Here's what's in it now:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>[COLOR="Red"]rgb[/COLOR]</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>[COLOR="#ff0000"]true[/COLOR]</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>[COLOR="#ff0000"]hintslight[/COLOR]</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>[COLOR="#ff0000"]true[/COLOR]</bool>
  </edit>
 </match>
</fontconfig>
```

Basically, what do I need to do to .fonts.conf to make it match my gnome settings (included in the screenshot below)
Also, how can I force 98 DPI?  Do I use .fonts.conf for that as well?  Any help is appreciated.

---

### Post by jordanmthomas on 2007-09-15
I'm not one to bump usually, but I don't want this one to get lost in the sea of old threads.

---

### Post by jordanmthomas on 2007-10-01
bi-weekly bump perhaps?

---

### Post by jordanmthomas on 2007-11-09
One last bump before I give up.
Don't make me cry guys.  :)

---

### Post by jordanmthomas on 2007-11-13
Ok, I have semi-solved my own problem I suppose.
I used the lcd patches for freetype and cairo and now my fonts look good even without gnome-settings-daemon.

As for the 98 DPI, I learned quite a while ago that that is done in xorg.conf.

It *is* a shame that I didn't get help over the course of over two months though.

---

### Post by jranweil on 2007-11-17
I just saw your post for the first time today.  What problems do you have left to solve?  I'm no hotshot, but I'll share anything I've picked up that could help.

---

### Post by jordanmthomas on 2007-11-18
Well, all my problems are gone now.  I don't need gnome-settings-daemon to get good looking fonts because I recompiled the font renderer to make them look nice without it.

I think the changes I would have needed to make would be to /etc/fonts/fonts.conf but I didn't know what to change to make them work like the settings I had in the gnome settings (from screenshot).  I'm still unsure as to what I need to edit, basically.  Luckily, the new font rendering looks BETTER than what I had with Gnome, so I am a happy camper now.

---

### Post by danf_1979 on 2008-01-11
Hi, could you please elaborate on what you did? I'm on kde4 now and gnome-fonts look like crap :)

---

### Post by jordanmthomas on 2008-01-11
Well, before I get into it too much, here's a screenshot so you can see if you like it (sorry about the jpg compression, it makes some of the fonts look a little bad).  If you think it looks horrible, you might want to skip the next paragraph.  Konqueror's on the left and Nautilus the right.  I don't particularly like the font I'm using at the moment, but it does render nicely I think.

I recompiled cairo and libxft with some patches cooked up by Gentoo people (note that Ubuntu has some pretty decent default font rendering with similar patches applied)  I tried Ubuntu's patches before xeffects' but I like xeffects' fonts better I think.

Then, I made a file called .gtkrc-2.0 in my home directory.
Here are its contents:
```
include "/home/jordan/.themes/oxygen/gtk-2.0/gtkrc"

style "user-font" {
        font_name = "Corbel 8"
}

widget_class "*" style "user-font"

gtk-font-name="Corbel 8"

include "/home/jordan/.gtkrc.mine"
```
This sets my gtk theme (oxygen) and a font (Corbel from Office 2007)
This will at least save you from having to use some humoungous font that gtk defaults to.  Also, you can use a program called gtk-chtheme to create this .gtkrc-2.0 file for you (I did).

Without the patches, the fonts were still rendered pretty poorly.  Unfortunately, I don't know much about packaging things up for Ubuntu so aside from manually applying the patches I don't know how to get the same font rendering I have into Ubuntu.
patches can be found here:  
cairo:  [http://aur.archlinux.org/packages/cairo-xeffects/cairo-xeffects/cairo-1.4.12-newspr.patch](http://aur.archlinux.org/packages/cairo-xeffects/cairo-xeffects/cairo-1.4.12-newspr.patch)
libxft:  [http://aur.archlinux.org/packages/libxft-xeffects/libxft-xeffects/libXft-2.1.12-dont_interfere_with_newspr.patch](http://aur.archlinux.org/packages/libxft-xeffects/libxft-xeffects/libXft-2.1.12-dont_interfere_with_newspr.patch)

I never could figure out what to put in font.conf to get the proper subpixel rendering and slight hinting like I like to use in Gnome.  I'm pretty sure if KDE isn't running my Gnome fonts still don't look so great (ie if I use awesome or some other window manager)

---

### Post by jordanmthomas on 2008-01-18
An update:  I figured out how to get subpixel hinting without KDE / Gnome.
Thanks to ~LoKe for unknowingly giving me an answer to my question.

Put something like this in your .Xdefaults:
```
!Xft settings
Xft.dpi:                96
Xft.hinting:            1
Xft.hintstyle:          hintslight
Xft.antialias:          1 
Xft.rgba:               rgb
```

---

