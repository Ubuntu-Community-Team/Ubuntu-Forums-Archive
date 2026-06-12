---
title: "Window Managers et al.."
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by markr on 2006-03-22
I've recently been playing with XGL and Compiz etc, when I suddenly realised I don't know much about how how Gnome, X etc actually fit together.

I've been googling around, bu can't find a decent guide on this.

What I'm interested in is finding out more about how all this 'X' stuff fits together,  for example I keep seeing discussions about composite managers, desktop decorators, metacity etc, without really knowing anything about them or how they all work together to provide the 'desktop experience'

any links available?

Mark.

---

### Post by shof2k on 2006-03-22
Hi,
I can't give you a full picture because I'm new to all this, but I'll share what I already know.

'X' is the graphical engine that gives you your graphical experience.  It started off as XFree86, but evolved to Xorg.  X uses diffrerent drivers to get your graphical hardware working to it's best ability.

Composite manager is a new feature to Xorg, that allows different images to be merged or composited together. The classic example is of translucent windows where you can see your desktop within your application.  Here X calls the composite manager to superimpose the desktop background onto the application (at a performance cost of source). 

X is used to create a whole graphical desktop. There are 2 major flavours, Gnome and KDE along with a whole host of other flavours such as XFCE, IceWM etc.

You can customise the graphical desktop to have different styles of windows, icons, wallpaper.  I think metacity is a particular style of Gnome.

I'm sure others will add to your overview.

Hope that helps,

---

