---
title: "Alternatives to Conky"
date: 2011-05-17
forum: Any Other OS
---

### Post by strike105x on 2011-05-17
Hi i'm using Linux Mint 9 and would like to know some alternative to Conky (because it doesn't work properly with Compiz wallpaper plugin). I'm interested in something that shows has a system monitor uptime, and would be great if it was transparent.

Edit: i'm  referring to some kind of docklet or widget or something.

---

### Post by Copper Bezel on 2011-05-17
Well, Screenlets comes with some hardware sensors, but not an uptime ticker, and if you're using Gnome Panel, you can use sensors-applet for roughly the same insufficient options. = P I can't find anything *but* Conky to display an uptime ticker. 

There's a community Compiz plugin called Greenscreen that's apparently still updating and is supposed to be able to apply real transparency to something like Conky, sort of top-down, but I couldn't make it work from git.

The best I've been able to figure out is to just turn off Conky's undecoration in the .conkyrc and set own_window_color to the GTK application background, then make class=Conky a non-movable window in Compiz, so that it just looks like another window hanging out there.

---

### Post by wildmanne39 on 2011-05-17
> **strike105x said:**
> Hi i'm using Linux Mint 9 and would like to know some alternative to Conky (because it doesn't work properly with Compiz wallpaper plugin). I'm interested in something that shows has a system monitor uptime, and would be great if it was transparent.

Edit: i'm  referring to some kind of docklet or widget or something.

Hi, I have conky working with compiz, I did have a problem when I first starting using conky it has to be set to start after compiz, if you did not set yours to do that I can tell you how to.

---

### Post by Copper Bezel on 2011-05-17
He's talking about Compiz *Wallpaper*, which requires turning off the Nautilus desktop. 

Conky draws its background by duplicating it from the root window, and if you're using Compiz Wallpaper, as strike105x is (and as I am,) the root window background is empty (or, rather, whatever detritus is left over from the GDM screen.) 

The reason Conky has to be delayed under Compiz Gnome is that the root window isn't drawn in time (by Nautilus) for Conky to catch it; if you're not using the Nautilus wallpaper in the first place, it doesn't really matter how long you wait for it. = )

---

### Post by wildmanne39 on 2011-05-17
> **Copper Bezel said:**
> He's talking about Compiz *Wallpaper*, which requires turning off the Nautilus desktop. 

Conky draws its background by duplicating it from the root window, and if you're using Compiz Wallpaper, as strike105x is (and as I am,) the root window background is empty (or, rather, whatever detritus is left over from the GDM screen.) 

The reason Conky has to be delayed under Compiz Gnome is that the root window isn't drawn in time (by Nautilus) for Conky to catch it; if you're not using the Nautilus wallpaper in the first place, it doesn't really matter how long you wait for it. = )
Hi, I see I mess read the question, my blood sugar is low right now so I am a little confused. I am sorry didnt mean to create confusion.

---

