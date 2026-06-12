---
title: "New IceWM Theme- IceOSX"
date: 2006-12-27
forum: Art &amp; Design
---

### Post by Albi on 2006-12-27
As per request, I made a mac clone theme.  I made two versions; a regular one and a blue one.  It's mostly bug free, although I'm trying to make the edges rounder.  Enjoy!

[[IMG]http://img86.imageshack.us/img86/1193/screenshot2006122718595ro3.th.jpg[/IMG]](http://img86.imageshack.us/my.php?image=screenshot2006122718595ro3.jpg)

Update 1: Panel updated to this:
[img]http://img118.imageshack.us/img118/4162/screenshot40aq3.jpg[/img]

And the wallpaper:
[http://img184.imageshack.us/img184/8348/osxoq5.jpg](http://img184.imageshack.us/img184/8348/osxoq5.jpg)

---

### Post by finferflu on 2006-12-28
Cool! Thanks! That's my theme now, the only thing I don't particularly like is that blue on the taskbar, I think it should be a bit lighter.. I don't know whether the OSX theme looks like that, but I don't particularly like it. Could you point me out how to change that please? Thanks!

It looks very cool with my desklet! :D

---

### Post by Albi on 2006-12-28
Changed to this now
[img]http://img118.imageshack.us/img118/4162/screenshot40aq3.jpg[/img]

(Mods: I realized this post is redundant, delete if you want)

---

### Post by finferflu on 2006-12-28
Ok, thank you! 

By lighter I meant "softer", by the way...

---

### Post by Albi on 2006-12-28
Is something like this alright?
[IMG]http://img397.imageshack.us/img397/8659/screenshot20xp1.jpg[/IMG]
or
[IMG]http://img297.imageshack.us/img297/958/screenshot31ul0.jpg[/IMG]

Pick one and I'll change it.

---

### Post by finferflu on 2006-12-28
The first one! and if you can, even slightly softer, but just very slightly. Sorry if I'm being too perfectionist...

---

### Post by Albi on 2006-12-28
No I understand, I forgot to realize the blue doesn't look nice if your wallpaper is not OSX

Updated now to this:
[img]http://img118.imageshack.us/img118/4162/screenshot40aq3.jpg[/img]

---

### Post by meborc on 2006-12-28
> **finferflu said:**
> Cool! Thanks! That's my theme now, the only thing I don't particularly like is that blue on the taskbar, I think it should be a bit lighter.. I don't know whether the OSX theme looks like that, but I don't particularly like it. Could you point me out how to change that please? Thanks!

It looks very cool with my desklet! :D

i just have to say i love your desktop... i have been using gnome/kde/xfce mainly, but now i'm looking into fluxbox/icewm etc... and i REALLY want to know how you got yours looking like this... what how-to did you follow? where did you learn about the desklet and how to play around with it? :-k

---

### Post by finferflu on 2006-12-28
> **Albi said:**
> No I understand, I forgot to realize the blue doesn't look nice if your wallpaper is not OSX

Updated now to this:
[img]http://img118.imageshack.us/img118/4162/screenshot40aq3.jpg[/img]

Thanks a lot! It looks perfect now!!

> **meborc said:**
> i just have to say i love your desktop... i have been using gnome/kde/xfce mainly, but now i'm looking into fluxbox/icewm etc... and i REALLY want to know how you got yours looking like this... what how-to did you follow? where did you learn about the desklet and how to play around with it? :-k

Thank you!
I did not follow any how to, I basically learnt things by reading instructions for every tool I used. 
As for IceWM, there are some tutorials on the [official website]("http://www.icewm.org/"), even though you basically need to download tools like icecc (IceWM Control Center - it's in the repositories), that graphically let you customise your settings, there are also similar ones, like iceme (IceWM Menu Editor), icepref, and so on. I can't remember which script has created the preferences file. I'll just post mine file, so you can look at my customisations, and eventually copy it if you don't want to install the graphical customisation aids. The theme is obviously IceOSX (thanks again Albi!).

As for the adesklets, I've found them googling for "Icewm eyecandy", and I've found out they're in the repositories. The only one I've used is called Yab, and you can download it on the [adesklets website]("http://adesklets.sourceforge.net/desklets.html"). To use and configure it, just read the instructions in the package (basically you just need to edit a very simple config file). If you have any trouble, just tell me, and I'll see how (and if) I can help you out. Just know that adesklets is like a server for the desklets, once you download a desklet, you need to register it with adeskets, so that when you start adesklet, they all appear. 

As for the startup (for example, if you want to startup adesklets automatically), you need to create a script that looks like this:
```

#!/bin/sh
adesklets&
```
name it startup and put it in the .icewm folder. If you use Gnome, I suggest you to put also update-notifier in it, if you use KDE, put adept_notifier. 

In addition to that, you could give a look at [this thread]("http://ubuntuforums.org/showthread.php?t=263710").

Have fun!

---

### Post by meborc on 2006-12-29
sweet... i'll get right on it as soon as i'm back at my ubuntu box... people usually misunderstand that lightness and eyecandy do not work well together... your desktop is a good example that it is not so :-D

---

### Post by finferflu on 2006-12-29
> **meborc said:**
> sweet... i'll get right on it as soon as i'm back at my ubuntu box... people usually misunderstand that lightness and eyecandy do not work well together... your desktop is a good example that it is not so :-D

Thanks!

@Albi

I just want to point out a couple of things. Is the tray bar (or whathever you call it) supposed to be black? Could that be of the same color as the toolbar? If not, could you tell me how to change it please?

Another thing is that the Window List (when you press CTRL+ALT+ESC) is all black, and I can't read anything unless I click on it.

Thanks a lot for your work and your patience :)

I'm posting the pictures of the toolbar and the window list.

---

### Post by Albi on 2006-12-29
I fixed the colours (it was based on a dark theme, so I forgot to change some of them).

However, the task bar tray is dependent on your gtk theme.  I tested this by changing every dark colour to light and it had no difference.

---

### Post by finferflu on 2006-12-29
Thanks!
Well, now the question is, how do you set a gtk theme on IceWM?

---

### Post by Albi on 2006-12-29
> **finferflu said:**
> Thanks!
Well, now the question is, how do you set a gtk theme on IceWM?

Use one with gnome and run gnome-settings-daemon on startup (2-3mb ram extra)

Edit: IT'S 2-3 MB not 23MB!

---

### Post by aysiu on 2006-12-30
Very sweet-looking! Thanks for porting this.

---

### Post by PurplePenguin on 2007-03-18
This is a bit of a late reply, but I just stumbled upon this new theme and really like it!  I still can't quite get gnome out of my system, but between this theme and icebuntu, I could definitely get used to IceWM... :)

---

### Post by lyceum on 2007-03-18
> **finferflu said:**
> Cool! Thanks! That's my theme now, the only thing I don't particularly like is that blue on the taskbar, I think it should be a bit lighter.. I don't know whether the OSX theme looks like that, but I don't particularly like it. Could you point me out how to change that please? Thanks!

It looks very cool with my desklet! :D

Is this gDesklets you have running at the top?

---

### Post by finferflu on 2007-03-18
No, it's aDesklets ;) It's very lightweight. You can find them in the repositories, and for more info: [http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

Enjoy!

---

### Post by lyceum on 2007-03-18
> **finferflu said:**
> No, it's aDesklets ;) It's very lightweight. You can find them in the repositories, and for more info: [http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

Enjoy!

cool, thanks!

---

### Post by Icy OS x on 2009-07-14
Hey,
I am working on a theme using cropped bits of a leopard screenshot. Will upload when done. Why has no-one done this????

---

### Post by Fzang on 2009-07-14
Don't revive old topics!

---

