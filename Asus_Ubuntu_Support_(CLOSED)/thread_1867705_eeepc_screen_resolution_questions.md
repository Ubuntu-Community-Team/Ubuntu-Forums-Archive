---
title: "eeepc screen resolution questions"
date: 2011-10-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Dan Gellert on 2011-10-23
Long-time Mac user, looking for something really portable and really cheap, got a used 1005 HAB, and have liked it pretty well, finding Windows not ideal but tolerable.   Just discovered wubi, and am slowly finding my way around the new world of Ubuntu...  I already know I won't be getting rid of it (if only for the no-brain-required networking!).

The main thing keeping me from dumping Windows is the problem of screen  resolution-- some apps just cannot be restricted to the 600 pixel vertical dimension of this netbook screen.  I find myself stuck in a preferences window, unable to access the exit buttons which are below the bottom of my screen.

I tried the script given at [https://help.ubuntu.com/community/EeePC/Using](https://help.ubuntu.com/community/EeePC/Using) and it does make the whole window visible, but the mouse pointer is still restricted to the area of the 1024x600 screen, so I still can't get to those buttons at the bottom.  Is there a fix for that?

If there is, I still don't much like the vertically-compressed look.  Under Windows (XP Home Edition), there is another option, for uncompressed 1024x768 resolution which pans up and down on the display.  That is what I'd really like to be able to do in Ubuntu.  Anyone out there figured out how to do that?

thanks

---

### Post by WasMeHere on 2011-10-23
Maybe we shouldn't call it a fix, but in most windows you can move the focus (the selected button) with tab (or sometimes the arrow keys), and then press it using Enter (or sometimes the space-bar). Try that until you find what you really want!

Have fun finding out about Ubuntu :-)
Olle

---

### Post by WasMeHere on 2011-10-23
Another possibility is to use two workspaces (desktop surfaces) above each other and let the high window continue from the top workspace to the bottom one. Then simply select the bottom workspace to see and press the buttons or edit text in combo boxes or whatever.

Example: In the attached picture, this very firefox window extends across both left workspaces (while t-bird fills the top right workspace and the fourth workspace is empty).

This is not what you asked for but it works fairly well :-)

Olle

---

### Post by Dan Gellert on 2011-10-23
Can that be done using Gnome Classic (which I like better than Unity)?  The workspaces don't seem to be contiguous as they are in Unity.  But then I only have 2 of them rather than 4 showing, and can't remember how to change that just now.... Would that make a difference?

---

### Post by WasMeHere on 2011-10-24
> **Dan Gellert said:**
> Can that be done using Gnome Classic (which I like better than Unity)?  The workspaces don't seem to be contiguous as they are in Unity.  But then I only have 2 of them rather than 4 showing, and can't remember how to change that just now.... Would that make a difference?
I am doing it with gnome classic.

1. If you don't have it already, you can add a tool to swap between workspaces to a panel.

2. Right-click on that tool and select 'Settings'.

3. Select 2 rows.

Now you should be able to let your windows extend across the border between a top workspace and a bottom workspace and you select the active workspace by left-clicking on its image on the tool on the panel.

I do not use 'the 3D cube' to shift between workspaces and I am not sure if it works in that environment.

---

### Post by Dan Gellert on 2011-10-24
> **Olle Wiklund said:**
> I am doing it with gnome classic.

1. If you don't have it already, you can add a tool to swap between workspaces to a panel.

2. Right-click on that tool and select 'Settings'.

3. Select 2 rows.

Now you should be able to let your windows extend across the border between a top workspace and a bottom workspace and you select the active workspace by left-clicking on its image on the tool on the panel.

I do not use 'the 3D cube' to shift between workspaces and I am not sure if it works in that environment.

I now have 4 workspaces in 2 rows (showing as a square in the right end of the lower panel), but they behave as entirely separate spaces-- a window partially moved off of the active workspace does NOT show up on any of the other 3.  I can move a window entirely onto another workspace using the panel, but can't make anything straddle the borders.

Been looking through the Configuration Editor for something that looks like it might relate to this, but no luck yet.   

Thanks again!

---

### Post by WasMeHere on 2011-10-25
It could be *different settings* but could also be *different versions* of the workspace manager, and they behave in a different ways. I use gnome 2 desktop environment because on my 'workhorse' computer I run Ubuntu 10.04 LTS. Another computer runs Ubuntu Studio 11.04. I run Unity only on a test partition with 'vanilla' Ubuntu 11.04. I can check with that one later on.

---

### Post by WasMeHere on 2011-10-25
It works also with Natty and Unity. See the attached screendump

Have fun finding out how to do it on *your* computer :-)
Olle

---

### Post by Dan Gellert on 2011-10-25
> **Olle Wiklund said:**
> It could be *different settings* but could also be *different versions* of the workspace manager, and they behave in a different ways. I use gnome 2 desktop environment because on my 'workhorse' computer I run Ubuntu 10.04 LTS. Another computer runs Ubuntu Studio 11.04. I run Unity only on a test partition with 'vanilla' Ubuntu 11.04. I can check with that one later on.


Maybe. I've got 11.10.

p.s. it does work just fine in the Unity workspace switcher.

---

