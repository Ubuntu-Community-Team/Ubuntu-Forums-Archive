---
title: "Another os x look-a-like."
date: 2008-10-12
forum: Art &amp; Design
---

### Post by Osborn on 2008-10-12
You know Mac4lin, it doesen't really look like mac. The menubar/objectbar is all wrong and many people puts loads of gadgets and stuff to the desktop.
Mac isn't like that, mac is clean.

I've been looking at the leopard guided tour a couple of times and I felt ready to do my own look-a-like. And so I did.

If you like it, I can make a guide later on , because I did only put applets and themes together. 
**Tell me if I should change something**

[IMG]http://i488.photobucket.com/albums/rr247/Osborn/Osbornsleopardesktop.png?t=1223807740[/IMG]

---

### Post by ronnielsen1 on 2008-10-12
Nice job, not really a Mac fan but it looks just like one

---

### Post by Osborn on 2008-10-12
> **ronnielsen1 said:**
> Nice job, not really a Mac fan but it looks just like one

Thank you!

---

### Post by Gutt on 2008-10-12
Great work Osborn :) . I'm no fan of the Mac look a like themes but this one's ok.

The only little problem I see in it is that Home Icon in the back window, seems to be sticking out a bit too much...

---

### Post by jorgecs10 on 2008-10-12
Great work!
Put this in the .gtkrc-2.0 file if you want to the scrollbars look like more how they look in mac os x

```
style "scrolledwindow-style" {    
    GtkScrolledWindow::scrollbar-spacing = 0
    GtkScrolledWindow::scrollbars-within-bevel = 1
}

style "scrollbar-style" {
    GtkScrollbar::has-backward-stepper = 0
    GtkScrollbar::has-forward-stepper = 1
    GtkScrollbar::has-secondary-backward-stepper = 1
}

class "GtkScrollbar" style "scrollbar-style"
class "GtkScrolledWindow" style "scrolledwindow-style"
```

---

### Post by The_OMFG on 2008-10-12
Mac wuhuuuuuu :)

---

### Post by Osborn on 2008-10-13
> **jorgecs10 said:**
> Great work!
Put this in the .gtkrc-2.0 file if you want to the scrollbars look like more how they look in mac os x

```
style "scrolledwindow-style" {    
    GtkScrolledWindow::scrollbar-spacing = 0
    GtkScrolledWindow::scrollbars-within-bevel = 1
}

style "scrollbar-style" {
    GtkScrollbar::has-backward-stepper = 0
    GtkScrollbar::has-forward-stepper = 1
    GtkScrollbar::has-secondary-backward-stepper = 1
}

class "GtkScrollbar" style "scrollbar-style"
class "GtkScrolledWindow" style "scrolledwindow-style"
```

Were do I find the gtkrc file?

---

### Post by meborc on 2008-10-13
please write a guide how to achieve this :)

i have played around with a mac look before, but i would like to scare the creeps out of my roommate (a mac lover)

btw, we have 3 people living in our flat right now... one using windows, one using mac and me... using linux

every day is like the youtube video :D

---

### Post by Genius314 on 2008-10-13
Just get rid of the little arrow on the menu icon, and stop the titlebar of the inactive windows from being transparent (unless this is a feature of OS X... it doesn't look too good).
Other than that, I think it looks great. :)

---

### Post by jorgecs10 on 2008-10-13
> **Osborn said:**
> Were do I find the gtkrc file?

Just look at [this tutorial]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes") and [this documentation page]("http://library.gnome.org/devel/gtk/stable/gtk-Resource-Files.html")

---

### Post by lian1238 on 2008-10-13
How did you get the menubar to be like mac? Is it Kubuntu? And what dock? I use cairo-dock and I love it!

---

### Post by Osborn on 2008-10-14
> **lian1238 said:**
> How did you get the menubar to be like mac? Is it Kubuntu? And what dock? I use cairo-dock and I love it!

**The menubar?** Oh it is just an applet.
You can get it by reading this: [http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

It can be tricky if you've never used the terminal ever before, but otherwise It's kinda easy. If you have any problems or anything just post it here and I'll help you.

**The dock?** I use the Avant Window Navigator, just search in the program-install-thing (synaptic) in ubuntu for Awn or Avant window navigator.

You will start with some skins. But you can download new skins to it like the one I use. I think you'll get the right Awnskin in Mac4lin (damn, haha).

---

### Post by ToasterThief on 2008-10-15
It's a damn shame the default look and feel, the default artwork and the desktop usability of Gnome and Ubuntu is so shitty that we have to go out of our way to make it look and feel like OS-X, XP or Vista. 

I's really a pity that we just can't come up with ideas and design ourself. I see this fact as a major factor in not being able to reduce the impact of Launchpad bug #1.

With KDE 4 Kubuntu 8.10 has actually beaten Ubuntu by miles and I find that irritating considering the majority of community and developer resources are allocated to Ubuntu. 

I had high hopes that Ubuntu 8.10 would fix some of the above, but I got sadly disappointed.

Ubuntu is still my favorite OS for stability and flexibility, but I'll rather selfinflict papercuts in my eyeballs than having to look at the default theme, however the solution is not to copy XP, Vista or OS-X.

---

### Post by lian1238 on 2008-10-15
> **ToasterThief said:**
> It's a damn shame the default look and feel, the default artwork and the desktop usability of Gnome and Ubuntu is so shitty that we have to go out of our way to make it look and feel like OS-X, XP or Vista. 

I's really a pity that we just can't come up with ideas and design ourself. I see this fact as a major factor in not being able to reduce the impact of Launchpad bug #1.

With KDE 4 Kubuntu 8.10 has actually beaten Ubuntu by miles and I find that irritating considering the majority of community and developer resources are allocated to Ubuntu. 

I had high hopes that Ubuntu 8.10 would fix some of the above, but I got sadly disappointed.

Ubuntu is still my favorite OS for stability and flexibility, but I'll rather selfinflict papercuts in my eyeballs than having to look at the default theme, however the solution is not to copy XP, Vista or OS-X.

The default look and feel is not "shitty", although it has that **[COLOR=Sienna]brown[/COLOR]** color (pun totally intended!). It's a unique look, different from the blue/purple of OS-X, the blue of XP, and the black of Vista. I like the default look & feel as it represents the "Ubuntu" philosophy, which has an African origin so it makes sense (the brown land, the brown animal hide that people used to wear, etc.) And if you hate it, change it! OS-X, XP, nor Vista provide the power of customization (themes and everything else) as much as Ubuntu.. not even close! You can find tons and tons of GPL'ed themes for Ubuntu.

---

### Post by Thricemin on 2008-10-16
Nice job it looks just like osx down to a T.

---

