---
title: "Panel gone"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Tyx on 2006-11-01
Please someone help. I switched my pc on and the ubuntu login
screen comes up as normal, then I log in, and I get a glimpse
of the ubuntu sign (nautilus?), then it goes, and that's it.
I have no panels, no icons, no nothing, they all disappeared
and I only get the mouse pointer on the brown background.
I don't know how that happened...can someone please help?
Thank you very much.
An absolute beginner.

---

### Post by Tyx on 2006-11-01
I should maybe also add that when I press the power button (it's a laptop), i get all the usual options of logging off etc. And pressing ctrl-alt-f1 gives me a command line and all my files are there and I can do whatever. But I want my panel back,
how do I do that from the command line? Maybe reset something...?
Anyone?

---

### Post by adam.tropics on 2006-11-02
Try <Alt>F2 then enter in the run dialogue 'killall gnome-panel' and see if you get the panels back. Failing that, are you able to log into failsafe mode?

---

### Post by Tyx on 2006-11-02
Unfortunately that doesn't work, alt-F2 doesn't do anything. The only thing I can do when in the desktop is press the power button and logout. It seems that my whole gnome is lost. I also tried from the command line(ctrl-alt-f1), after looking around in the forum to rename .config, .gnome(2), .nautilus, .metacity, .gconf and .gconfd, but nothing happened. 
I just remembered that before that happened, I installed kde-core from the repositories...I think that killed my gnome. Is there anyway to get it back?
Please?

---

### Post by Tyx on 2006-11-02
I went somewhere where I could get direct internet connection, and from the command line I tried apt-get install gnome and nautilus...nothing. I only get a brown background with a mouse pointer. Before I have to re-install ubuntu and lose all my downloads...can an expert please please help?? :(

---

### Post by ajackson on 2006-11-02
> **Tyx said:**
> I just remembered that before that happened, I installed kde-core from the repositories...I think that killed my gnome. Is there anyway to get it back?
If you think it want kde-core that killed gnome try:

sudo apt-get --purge remove kde-core

that should get rid of all traces of kde-core.

If that still doesn't work try:

sudo apt-get --reinstall install gnome-panel

---

### Post by Tyx on 2006-11-02
Thanks, I've done that already. The kde-core was removed, when I try to reinstall gnome-panel it says it's already the latest version and does nothing. Argh. Anyway, sometimes you have to cut your losses. At least I was able to save my files...it's just really annoying...I'll just reinstall it, and stay away from kde :P

---

### Post by ajackson on 2006-11-02
If you add the --reinstall it downloads the package and re-installs it even if you already have the latest version.

---

### Post by Tyx on 2006-11-02
> **ajackson said:**
> If you add the --reinstall it downloads the package and re-installs it even if you already have the latest version.

Thanks ajackson, it's too late now to try. It's ok, I did so many trials of stuff with my new ubuntu so I guess it's for the best, a clean install. And I'll keep the --reinstall tag in mind for the future...I'm not sure it would do anything though.

Have a nice evening :)

---

