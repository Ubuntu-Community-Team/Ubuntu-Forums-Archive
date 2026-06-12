---
title: "9800 pro and advanced effects"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-02-22
I've been trying to get reasonable performance out of my graphics card this last week but I'm really struggling. When I move Windows around the desktop they leave a trail behind them and sometimes leave a black square for a few seconds where the window has been until the screen refreshes. When I turn on the transparency option for the command line window it's really poor, it show me the wallpaper but when I move the window around it doesn't refresh properly.

I'm pretty sure that everything is installed correctly, when I type fglrxinfo at the command line it tells me I have the latest drivers installed and identifies the card correctly so I'm not sure what the problem is. The card itself is fine, it works nicely within Windows XP so it's not a hardware problem that I can think of. 

I have read here on the Ubuntu forums that Radeon cards just don't work that well with Ubuntu and the advanced effects like transparencies, drop shadows and fades etc (I think it's called XGL or something like that). Can anybody here confirm this? I really want to get these working but I don't want to buy a new graphics card just for this purpose unless I have to.


Anybody have a 9800 pro working with all of these effects in Ubuntu?

---

### Post by mostwanted on 2006-02-22
Metacity, the default window manager, doesn't have those effects... yet. You want to install a composite Window Manager like Compiz. For this you need to upgrade to Dapper which I wouldn't advice as it's very buggy (it's not released yet).

---

### Post by Estariel on 2006-02-22
It will probably take another year until all those fancy effects are really stable (in dapper they won't be officially supported but you can get them if you feel courageous).

In Breezy, you can enable the composite extension of the xserver, which will produce some nice acceleration and transparency effects, but it isn't stable either (and it doesn't have anything to do with Xgl). There is a how-to on this in the How-to section of the forums.

As far as I know, ATI graphics cards just don't work that well (with neither Xgl nor composite), since nvidias driver just is superior.
If you intend to stick with linux and you like eye candy, get an nvidia graphics card.

---

