---
title: "xterm and default colors and size"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by flux_user on 2008-03-28
Hello,
I am trying to change the the appearance of xterm in Ubuntu. My (limited) understanding is that I have to change either:
[LIST=1]
[*].xresources
[*].xdefaults
[*].xsession
[*].xsessionrc
[*].xinitrc
[/LIST]

I am having trouble  with the actual configuration to be read once I log into the system.  I am not sure if this makes  a difference; but the entries are:

[LIST]
[*]xft.antialias: true
[*]xft.hinting: true
[*]xft.rgba: rgb
[*]xterm*SaveLines: 1000
[*]xterm*background: black
[*]xterm*font: 9x20
[*]xterm*foreground: orange
[*]xterm*leftScrollBar: false
[*]xterm*rightScrollBar: true
[/LIST]

PS: from what I remember, I also have to xrdb -merge  -load $/HOME/xxxx.

Any help would be greatly appreciated.
TIA.

---

### Post by jan quark on 2008-03-28
perhaps you will find the answers here:
[http://linuxhelp.blogspot.com/2005/10/configuring-xterm-in-linux.html](http://linuxhelp.blogspot.com/2005/10/configuring-xterm-in-linux.html)

---

### Post by kerry_s on 2008-03-28
i use ~/.Xdefaults
you'll need to put> xrdb -merge ~/.Xdefaults 
in your startup to load it at start.

```

!! you should run> xrdb -merge ~/.Xdefaults 

*customization: -color

Xft.dpi: 75
Xft.antialias: true
Xft.hinting: true
Xft.hintstyle: hintfull
Xft.rgba: vrgb

Xcalc*geometry: 250x300

Xman*Font: -*-fixed-*-*-*-*-20-*-*-*-*-*-*-*

Xmessage*Font: -*-fixed-*-*-*-*-20-*-*-*-*-*-*-*

Xedit*geometry: 1000x600
Xedit*fontSet: -*-fixed-*-*-*-*-20-*-*-*-*-*-*-*
Xedit*enableBackups: off
Xedit*editWindow.scrollHorizontal: true
Xedit*Scrollbar.thumb: wide_weave
Xedit*hScrollbar.thumb: wide_weave

XTerm*faceName: Monospace
XTerm*faceSize: 14
Xterm*scrollBar: false
Xterm*saveLines: 5000
Xterm*background: black
Xterm*foreground: white
Xterm*utf8: 1

```

---

### Post by flux_user on 2008-03-28
[I]"i use ~/.Xdefaults
you'll need to put> xrdb -merge ~/.Xdefaults
in your startup to load it at start.[/I]"

Hello I did put xrdb -merge ~/.Xdefaults into .Xdefaults.  No luck; it hasn't changed the appearance of xterm.  What you you have in your .Xinitrc?

TIA

---

### Post by kerry_s on 2008-03-28
> **flux_user said:**
> [I]"i use ~/.Xdefaults
you'll need to put> xrdb -merge ~/.Xdefaults
in your startup to load it at start.[/I]"

Hello I did put xrdb -merge ~/.Xdefaults into .Xdefaults.  No luck; it hasn't changed the appearance of xterm.  What you you have in your .Xinitrc?

TIA

no no, put "xrdb -merge ~/.Xdefaults" in your startup file. you can also run that in terminal to get the effects right away.
i only have it in xdefaults to remind me.

in ubuntu your startup is that session manager thing.

my ~/.xinitrc is not going to help you it's used to start my window manager, jwm, i have jwm set to run my startup. i'm not using a log in manager and i'm also using debian.

wait what are you using? gnome, kde, xfce4, fluxbox
cause i see your name "flux_user" if your using fluxbox, your startup is> ~/.fluxbox/startup
put it in there with "&" on  the end
example:
xrdb -merge ~/.Xdefaults &

---

### Post by flux_user on 2008-03-29
Thank you very much.  I have xterm launching in accordance with .Xdefaults.  

PS: Yes, I am using fluxbox.  I still have  to get anti-aliased fonts working.  I will post under another thread.  Once again; THANKS A LOT!!

---

### Post by kerry_s on 2008-03-29
> **flux_user said:**
> Thank you very much.  I have xterm launching in accordance with .Xdefaults.  

PS: Yes, I am using fluxbox.  I still have  to get anti-aliased fonts working.  I will post under another thread.  Once again; THANKS A LOT!!

make sure when you ask for help you say your using fluxbox, there are ton's of fluxbox users here, you'll get help right away. i'm a X fluxbox user.

fonts-> [http://fluxbox-wiki.org/index.php/Style_overlay](http://fluxbox-wiki.org/index.php/Style_overlay)

use anti aliased font, aka: ttf font, such as dejavu sans

---

