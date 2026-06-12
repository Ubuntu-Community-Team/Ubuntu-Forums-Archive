---
title: "An interesting dilemma (fluxbox, pcmanfm)"
date: 2008-03-29
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-03-29
In pcmanfm's options, I chose a background image for my wallpaper.  It looks good, but now I don't get fluxbox's menu when I right-click on my desktop.  If I close this browser, I actually have no way of launching any programs haha.  You can see that I'm in quite a mess.  How can I fix this?  I'm running Arch, btw.

---

### Post by kerry_s on 2008-03-29
use fbdesk, it's made for fluxbox desktop icons. let fluxbox do the background as usual through the startup or overlay( [http://fluxbox-wiki.org/index.php/Style_overlay](http://fluxbox-wiki.org/index.php/Style_overlay) )
[http://fluxbox.sourceforge.net/fbdesk/](http://fluxbox.sourceforge.net/fbdesk/)

or use rox-filer instead, it's smaller, faster, more configurable and it has the compatibility setting to pass the right click.
put> rox -s & <in your ~/.fluxbox/startup

---

### Post by K.Mandla on 2008-03-29
> **TheOrangePeanut said:**
> In pcmanfm's options, I chose a background image for my wallpaper.  It looks good, but now I don't get fluxbox's menu when I right-click on my desktop.  If I close this browser, I actually have no way of launching any programs haha.  You can see that I'm in quite a mess.  How can I fix this?  I'm running Arch, btw.
I've noticed that before in Openbox too. I think it's because [PCMan]("http://ubuntuforums.org/member.php?u=164092") intended that file manager to run alongside the rest of that desktop suite, which means lxpanel would handle most of the work of the right-click menu.

You might consider filing a bug report with him, since it does seem counterintuitive. Or you might PM him and see if he can give you an idea; he's active around here from time to time. (And he writes great software, by the way.)

I'll move your thread to the Arch section, since you're using Arch. :)

---

### Post by urukrama on 2008-03-29
You could add a keybinding for the desktop menu in the keys file. Something like the following:

> Mod1 F1	:RootMenu

This will bring up the root menu when the keys Alt and F1 are pressed.

---

### Post by eriqjaffe on 2008-03-30
There's an option hidden in the PCManFM desktop preferences to "show WM menu with right click" which may be causing problems.

---

### Post by webaake on 2008-04-02
I have the same dilemma on Openbox/LXDE with pcmanfm. Default I have some one colored background, but after starting pcmanfm from lxpanel it takes over the whole desktop with icons, colors and wallpaper and obmenu isn't available. I have to kill it to be able to use obmenu again.

It seems a bit strange that a file manager acts as desktop, or have I misundertood pcmanfm ?? Is there a way to fix this.

I run Openbox 3.4.6.1, pcmanfm 0.3.6.2, lxsession-0.3.2
, lxde-common-0.3.0.1 and lxpanel 0.2.9.0.

---

### Post by webaake on 2008-04-02
Solved it! I unclicked the option "show desktop icons" in preferences and it now functions as filemanager should do, in my opnion.

I'm not much for desktop icons cluttering the desktop anyway, and pcmanfm IS really fast!

Thx pcman!

---

