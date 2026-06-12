---
title: "Transparent system panel applets"
date: 2004-12-13
forum: Art &amp; Design
---

### Post by bob k on 2004-12-13
I've got all of my systems work done and decided to take a break have some fun and work on eye candy. Since I'm fairly new new to this side of Linux I tried to keep it simple. I installed the industrial theme with crystal icons and some of the PSI gdesklets, and have set every thing transparent.

What I would like to do is set the system panel applets to transparent and change the color of the font to white. The applets that I'm talking about are the volume control, trash can, application computer, task list, and the window switcher. I've been googling for a day or two and haven't got very far, but I have learned allot about GTK, panels, applets, and widgets.

From every thing I've read it looks like I'm going to have to do some work in my themes gtkrc and maybe X11, but gtkrc documentation is very thin at best, and thought if somebody's been down this road they could get me on the right track.

Tia
Bob

---

### Post by bvc on 2004-12-13
those applets don't do trans
if you change the fg color of the panel you change it everywhere
welcome to limited gtk :-(

---

### Post by bob k on 2004-12-13
[QUOTE=bvc]those applets don't do trans
if you change the fg color of the panel you change it everywhere
welcome to limited gtk :-([/QUOTE]

I kinda figured that was the answer. It looked like they were creating the applets in code with a text title and letting gtkrc supply the icon, fg, and bg color, maybe next year. I also noticed the SVG icons are still a little buggy.

---

### Post by bvc on 2004-12-13
I've never had a prob with svg icons

---

### Post by bob k on 2004-12-14
[QUOTE=bvc]I've never had a prob with svg icons[/QUOTE]

I was getting allot of errors in my Xsessions file from gedit, nautilus, and gdk manager like below.

(gnome-theme-manager:19457): Gtk-WARNING **: Theme directory  of theme ICON-Crystal-SVG-1.1.0 has no size field

When I changed fonts all of that stopped.

EDIT

I figured out what the problem was, when I was setting up my gdesklets I dropped a couple where they should not have been, and were hidden. The only way I found them was a small white bar 10 or 20 pix long on my screen.

So I right clicked until I got a gdesklet menu and removed the applet.

My error was I navigated to the .display file and tried to let mime handle it, but if you don't move it and set it  , you will get burned.

Anyway these are fun problems.

Bob

---

### Post by Daniel G. Taylor on 2004-12-14
As far as I know this issue is being worked on by the GNOME developers.

I think a lot more of this sort of stuff will fall into place when the majority of people start to use compositing (well, when it's stable enough for most people).

---

### Post by piedamaro on 2004-12-15
[QUOTE=Daniel G. Taylor]As far as I know this issue is being worked on by the GNOME developers.

I think a lot more of this sort of stuff will fall into place when the majority of people start to use compositing (well, when it's stable enough for most people).[/QUOTE]
 I've read at 'break my gentoo' about the latest gnome applets version supporting translucency.

---

