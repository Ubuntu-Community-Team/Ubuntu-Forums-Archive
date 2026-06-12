---
title: "The XFCE thread..."
date: 2008-11-10
forum: Arch and derivatives
---

### Post by mips on 2008-11-10
I just formatted my notebook and reinstalling Arch. I intend to install XFCE as the DE.

What I would like to know is what applications people use in XFCE for normal use. Stuff like torrent client, cd/dvd burner, web browser etc.

Any good themes that have narrow title bars for windows etc. The default theme seems to take up to much real estate.

---

### Post by mali2297 on 2008-11-10
See [http://wiki.xfce.org/recommendedapps](http://wiki.xfce.org/recommendedapps)

The browser **midori** is now a 'Xfce Goodie'. It might be worth a try.

For a minimal xfwm4 theme, check out [prelude-4](http://xfce-look.org/content/show.php/prelude-4?content=69300).

---

### Post by ratmandall on 2008-11-10
> **mips said:**
> I just formatted my notebook and reinstalling Arch. I intend to install XFCE as the DE.

What I would like to know is what applications people use in XFCE for normal use. Stuff like torrent client, cd/dvd burner, web browser etc.

Any good themes that have narrow title bars for windows etc. The default theme seem to take up to much real estate.

Just use firefox, transmission etc.. same as gnome in ubuntu.

---

### Post by mips on 2008-11-10
> **ratmandall said:**
> Just use firefox, transmission etc.. same as gnome in ubuntu.

Lol, that's part of my problem, I have not touched Gnome in years. I'm a KDE user most of the time so this is all foreign to me. I'm used to K3B, K9copy, Dolphin, Ktorrent etc.

---

### Post by chucky chuckaluck on 2008-11-10
the kupo window decorations are 'normal' sized and are beautiful. you can get them from xfce-look.org.

one thing that irritates me about xfce is not being able to load a wallpaper from thunar. that seems almost immoral to me.

---

### Post by SomeGuyDude on 2008-11-10
I don't use XFCE but I use all GTK apps, so here goes.

Browser: Firefox. I've tried all the forks and everything else, but I never stick with 'em long.

Torrents: rTorrent. I run it on another workspace. It's perfect. CLI, though.

Disc burning: Brasero

Video: Gnome-Mplayer (actually doesn't require GNOME libraries)

Music: MPD + GMPC

Chat: Pidgin

Anything I missed?

---

### Post by fwojciec on 2008-11-10
EDIT: Post removed.

---

### Post by handy on 2008-11-10
I use the following:

Transmission - torrents
Firefox -
Mousepad - text editor
Mirage - image viewing
Gcolor2 - colour ID tool 
NeroLinux -
VLC -
FileZilla - ftp
Vidalia - Tor & Privoxy GUI
Zenmap - network & security exploration
ePDFviewer -
DVDshrink3.2 - ripping DVD's
Smartripper - when DVDshrink has difficulty
GParted -
htop - process observation & elimination :-)
emelfm2 - dirutil
squeeze - & associated (de)compression tools
ROX Filer - dirutil

I also use some from the [***_XFCE-Goodies_***]("http://goodies.xfce.org/") project.

---

### Post by handy on 2008-11-10
> **fwojciec said:**
> You can use thunar's ability to define custom actions to be able to set the wallpaper from thunar right click menu.  This is a script that I user for this (requires zenity and feh):

```
#!/bin/sh
# set_wall.sh

METHOD=`zenity --list --title="Set wallpaper..." --radiolist --column="Set" --column="Scale method" TRUE Scale FALSE Tile FALSE Center`

case $METHOD in
    Scale)
    feh --bg-scale "$1"
    ;;
    Tile)
    feh --bg-tile "$1"
    ;;
    Center)
    feh --bg-center "$1"
    ;;
    *)
    exit 1
    ;;
esac
```

Save it as set_wall.sh somewhere in $PATH, make it executable, and add a custom action in thunar:

Name: Set Wallpaper
Description: Whatever
Command: set_wall.sh %f

In "Appearance Conditions" tab set "Image Files".

It tries hard to work, but all I get is a grey background, no pic, I have tried the 3 different options with no change.

Another side effect is that I have lost my RMB desktop menu in xfce which is all but a show stopper. :lolflag: 

My screen is 24" running 1920x1200

[Edit:]  I just ctrl alt backspaced out of trouble, but on the way there was a flash of the chosen wallpaper?

I wonder what is blocking the image display?

---

### Post by fwojciec on 2008-11-10
> **handy said:**
> It tries hard to work, but all I get is a grey background, no pic, I have tried the 3 different options with no change.

Another side effect is that I have lost my RMB desktop menu in xfce which is all but a show stopper. :lolflag: 

My screen is 24" running 1920x1200

[Edit:]  I just ctrl alt backspaced out of trouble, but on the way there was a flash of the chosen wallpaper?

I wonder what is blocking the image display?

I installed xfce (I normally use thunar with openbox or compiz-fusion standalone) and I was able to confirm that feh doesn't play nice with some part of xfce that's responsible for drawing the desktop.  I'll remove the script from the above post, to avoid confusion.  The experience of loosing right click menu when feh sets the wallpaper can be a bit disconcerting, I suppose.

Sorry for the trouble caused by this solution.

---

### Post by handy on 2008-11-10
> **fwojciec said:**
> I installed xfce (I normally use thunar with openbox or compiz-fusion standalone) and I was able to confirm that feh doesn't play nice with some part of xfce that's responsible for drawing the desktop.  I'll remove the script from the above post, to avoid confusion.  The experience of loosing right click menu when feh sets the wallpaper can be a bit disconcerting, I suppose.

Sorry for the trouble caused by this solution.

Thanks for your incredibly quick reply. 

I thought I may have done something unusual (unconsciously) in the system which was the cause of it.

When you know you don't know much, you don't know what effects you may have unknowingly caused by something that you didn't know that you did... :lolflag: ***[Edit:]** I'm referring to my ignorance, certainly not yours fwojciec* :-)

---

### Post by cardinals_fan on 2008-11-10
Xfce is my second choice, behind dwm.  I think it's very good.

I use the same apps I'd use anywhere:

* vim
* urxvt
* gqview
* vimperator
* conky
* leafpad (mousepad is included with Xfce and does the same stuff)
* notecase
* consonance
* emelfm2
* clex
* alpine
* xpad

---

### Post by kk0sse54 on 2008-11-10
When I go for a full fledged DE xfce is always there for me :)

-Opera
-Pidgin
-Nicotine+
-Brasero
-Songbird
-Sonata
-Tilda
-Cairo-Clock
-Mousepad
-Abiword
-Squeeze
-and file management is between Thunar and Pcmanfm
-plus all those nice CLI apps: Irssi, rTorrent, Vim etc etc

I think that's everything :-k

---

### Post by mips on 2008-11-11
Just some feedback so far. I have a fresh install of arch+xfce+firefox+plugins/codecs, no other apps yet.

First thing I did was change my fonts to bitstream vera sans as the default ones are horrid.

I find the Panel extremely annoying as it takes up real estate on my 1024x768 display and would like to somehow integrate it with the Taskbar so I only have a single thin panel/taskbar. Is this possible?

After that I will have to change the Icons to nicer ones. I also hate how the icons have a border/bubble around the name of the icon, I suspect this is a setting I can change somewhere.

After the icons will be looking for some nice themes. Thanks for the suggestions so far.

Thunar is a POS, reminds me of Nautilus. Suppose I will have to use emel2fm. I wish there was an equivalent to Dolphin or Konqueror.

---

### Post by mali2297 on 2008-11-11
> **mips said:**
> 
I find the Panel extremely annoying as it takes up real estate on my 1024x768 display and would like to somehow integrate it with the Taskbar so I only have a single thin panel/taskbar. Is this possible?


Do you mean that you want to reduce the number of panels from two to one?

If so, just remove one of them and add items such as a tasklist to the other one. Right-click on the panel and there will pop up a settings menu. You can adjust position, size and transparency via Customize Panel.

---

### Post by handy on 2008-11-11
Mips, there are apparently ways to make the panel(s) background transparent leaving the icons & what have you visible.  I'll have a look for details on this, the transparency available in Customize Panel is only good for the intensity of the entire panel.

I really enjoy using XFCE it is quick & simple to do everything, with the exception of a few areas that are still handled in a clumsy fashion: 

Editing the menu 

Installing/managing themes

Modifying the colours of text & backgrounds  

I spent some hours yesterday after doing some house work & deleting everything to do with Openbox, trying to find a dark theme that suited my eyes & taste.

I have a compromise that I can live with, but it is not how I would do it for myself.

I'll post some theme links below, something you may or may not know when you are using GTK2 themes, create  ~/.themes & unpack any themes you want to test out into that directory, as it takes precedence over the other one in /usr/share/themes & you have the benefit of not having to go to root:
[I][U]
[http://art.gnome.org/themes/gtk2/](http://art.gnome.org/themes/gtk2/)

[http://jp.bizet.free.fr/themes/gtk2.html](http://jp.bizet.free.fr/themes/gtk2.html)

[http://www.archlinux.org/packages/extra/i686/gtk2-themes-collection/](http://www.archlinux.org/packages/extra/i686/gtk2-themes-collection/)

[http://daelstorm.thegraveyard.org/themes.php](http://daelstorm.thegraveyard.org/themes.php)

[http://www.linuxhaxor.net/2008/10/10/10-finger-licking-linux-desktopthemes/](http://www.linuxhaxor.net/2008/10/10/10-finger-licking-linux-desktopthemes/)

[http://www.ubuntu-art.org/index.php?xcontentmode=100&PHPSESSID=f88a7c779d53c33f7aa368f741f1af62](http://www.ubuntu-art.org/index.php?xcontentmode=100&PHPSESSID=f88a7c779d53c33f7aa368f741f1af62)[/U][/I]


The following link is good for a basic understanding of the pain in the RRRs that modifying themes is, no matter what DE/WM you are using:

*_[http://www.murga-linux.com/puppy/viewtopic.php?p=243476#243476](http://www.murga-linux.com/puppy/viewtopic.php?p=243476#243476)_*

This may also be useful to those who like to switch themes often:

*_[http://www.archlinux.org/packages/extra/x86_64/gtk-theme-switch2/](http://www.archlinux.org/packages/extra/x86_64/gtk-theme-switch2/)_*

---

### Post by chucky chuckaluck on 2008-11-11
in case the horse is just in a coma... when i still used thunar in openbox, i had custom actions set up, using feh, to load a wallpaper from my wallpaper directory. it was a very simple thing to do. someone on the xfce forum gave me some kind of hack to use it in xfce (not using feh) and it really didn't work well. i could only choose scaled, or tiled, but not both. one can load wallpapers from nautilus, konqueror and even gwenview (oh wait, that was in kde3). it seems this should be an easy thing in xfce. after all, what's the point of a DE if it can't do stuff like that?

---

### Post by handy on 2008-11-11
> **chucky chuckaluck said:**
> in case the horse is just in a coma... when i still used thunar in openbox, i had custom actions set up, using feh, to load a wallpaper from my wallpaper directory. it was a very simple thing to do. someone on the xfce forum gave me some kind of hack to use it in xfce (not using feh) and it really didn't work well. i could only choose scaled, or tiled, but not both. one can load wallpapers from nautilus, konqueror and even gwenview (oh wait, that was in kde3). it seems this should be an easy thing in xfce. after all, what's the point of a DE if it can't do stuff like that?

Horses for courses, I haven't used a screen background (apart form a black background) in Arch, ever. :popcorn:

I rarely look at the screen, only when flicking to another desktop to open something on it.

The next bug bear I have to squash is editing the colours of themes.  Which I intend to do real soon now.

---

### Post by chucky chuckaluck on 2008-11-12
> **handy said:**
> Horses for courses, I haven't used a screen background (apart form a black background) in Arch, ever. 

whenever i use tiling wm's (and it seems like it'll be for a while now), i get away from wallpapers, as well, but i don't think that excuses xfce from having the option of selecting a wallpaper from its file manager. integration between its major components is the only reason i can see for using a DE and this seems like a requirement to me (of course, i really can't see any reason to use a DE at all, so maybe it's pointless for me to even talk about it).

---

### Post by Koori23 on 2008-11-12
if you want to get rid of the panel completely

In your terminal type *kill xfce4-panel*

that'll kill it for your current session

If you want it to remain that way (nonexistent) you'll need to get to the logout screen

On the logout screen, check the "save session" box and logout and log back in, the panel won't be there anymore.

If you want the panel back, ALT+F2 -> xfce4-panel  save the session again

---

### Post by mips on 2008-11-15
I think I have come to the conclusion xfce is not for me, it just does not feel right.

I'll keep it on the laptop for a while and play with it but right now I'm installing kdemod 4.2.

Tanks for all the input, much appreciated.

---

### Post by chucky chuckaluck on 2008-11-15
> **mips said:**
> right now I'm installing kdemod 4.2.

kdemod has 4.2?!? (why did i read this? resist, resist, resist!)

---

### Post by medic2000 on 2008-11-15
Why do you like 4.2 that much? It is still very buggy and and not complete environment.

---

### Post by chucky chuckaluck on 2008-11-15
> **medic2000 said:**
> Why do you like 4.2 that much? It is still very buggy and and not complete environment.

i don't. i just need a break from dwm and terminal apps.

---

### Post by mips on 2008-11-15
> **chucky chuckaluck said:**
> kdemod has 4.2?!? (why did i read this? resist, resist, resist!)

Only in the unstable repo. I hit a snag though, [http://kdemod.ath.cx/bbs/viewtopic.php?id=1295](http://kdemod.ath.cx/bbs/viewtopic.php?id=1295)

It's still Alpha though.

---

### Post by cardinals_fan on 2008-11-15
> **chucky chuckaluck said:**
> i don't. i just need a break from dwm and terminal apps.
You mean you need a break from quality? :D

---

### Post by handy on 2008-11-15
> **cardinals_fan said:**
> You mean you need a break from quality? :D

You may be half right... ;-)

I shouldn't have said that, as Hagrid would say. :lolflag:

***[Edit:]** I think you may have missed the allusion to half left, being an temporary adversary in another thread... :-)*

---

### Post by chucky chuckaluck on 2008-11-16
> **cardinals_fan said:**
> You mean you need a break from quality? :D

oh no, using linux instead of windows me took care of that.

---

### Post by medic2000 on 2008-11-17
I just installed Xfce. Unlike Gnome it's blazing fast. But i have a problem with Turkish characters with usb drives like "&#287;,ü,&#304;,Ç" doesnt display correctly. How i can fix that. In Gnome i could solve it in gconf-editor.

---

