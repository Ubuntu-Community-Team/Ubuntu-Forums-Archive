---
title: "desktop question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-16
I have some questions about different desktops.  I have a semi-slow machine. (PIII 933 MHZ 512mb ram).  I would like to try out some other desktops.  I have read bout XFCE, ICEWM, Fluxbox etc...

Can I install mulitiple desktops, and then switch to which ever one I want?  If I do this, will I actually be slowing my machine down, because I have 2 different ones installed?

I see where ICEWM is just a window manager.  It says you can also install a desktop with this.  What is the difference between a window manager and a desktop?

If I use a different desktop, will I be able to run all the programs I am currently running with gnome?  (Especially the programs that start with "g" like gedit etc..)

Or say for example, I like everything about XFCE, but I want to use Nautilus as my file manager.  Is this possible?


Thanks

Tim

---

### Post by koconnor100 on 2007-02-16
Yeah , I saw screenies of a desk top that was some kind of rotating cube, and somone described to me a desk top that was like a stack of books being put in or coming out of a book case, very animated, where each book was a document you were working on. 

What are the alternatives to Gnome, and how stable are they ?

---

### Post by Sklasko on 2007-02-16
Well a window manager does just that, manages windows in X. A Desktop Environment ususally includes things like panels and other programs. Your best bet is either XFCE or Fluxbox, OpenBox, IceWM, etc.

As for the alternatives to GNOME, you have KDE and XFCE. Yes, both are just as stable and yes, all your programs will run in all other DE's or WM's.

Also, the rotating cube is Beryl (or Compiz?) which is a composite manager, an addon for desktop environments. Not recommended for low-spec machines or ATI users.

---

### Post by tim1970 on 2007-02-16
> **Sklasko said:**
>  Your best bet is either XFCE or Fluxbox, OpenBox, IceWM, etc.

As for the alternatives to GNOME, you have KDE and XFCE. Yes, both are just as stable and yes, all your programs will run in all other DE's or WM's.


I am confused.  First you mentioned XFCE, FLUXBOX, Openbox,ICEWM etc, then you said that the only alternatives to GNOME are KDE and XFCE.  Help :confused: 


Tim

---

### Post by Tyr Norian on 2007-02-16
You can indeed try different desktops/window managers and select them. It will take extra space on your drives, but it won't slow you down. Depending on your system you might find XFCE is surprisingly fast. And yes, Nautilus works under it, but Thunar, the default file manager, is pretty neat.

Install xubuntu-desktop and/or kubuntu-desktop using Synaptic or apt-get. Then reboot your system. Your default desktop and window manager will remain GNOME, but in your Sessions menu as you log in, you'll notice additional options available for XFCE and/or KDE respectively.

Installing packages blackbox or fluxbox by the same method will give you additional window managers. Blackbox in particular is absurdly efficient, but it has a bit of a learning curve to it.

I quite like XFCE, but I can't stand KDE. I stuck with GNOME in the end.

---

### Post by rocknrolf77 on 2007-02-16
You don't have to reboot to change desktop enviroment. You can just log out and select what session you want in the login manager. Or you can hit "ctrl - alt - backspace" to restart the x-server. :)

---

### Post by fuscia on 2007-02-16
you can mix and match more than most people probably realize. i've never found an app that would only work with one DE/wm. i've used kicker and xfce panels in openbox and fluxbox and all sorts of gnome and kde apps in all sorts of DE/wms. 

thunar is a great file manager (and can be used in all sorts of DE/wms. aysiu even has a script replacing nautilus with thunar as the default file manager in gnome), but if you want to use nautilus in DE/wms other than gnome, write the command as *nautilus --no-desktop*, unless you want nautilus to run your wallpaper.

---

