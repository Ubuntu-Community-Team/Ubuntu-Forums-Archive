---
title: "[SOLVED] I can run Gnome and KDE: How can I also run basic &amp;quot;X Windows&amp;quot; in a virtual p"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2008-02-09
I have an Ubuntu Feisty system that uses Gnome as its primary desktop manager (the one that "lives at" CTRL+ALT+F7).

I have also installed KDE "base" so that I can run KDE (via startx or via Gnome > Applications > System Tools > New Login) in a second virtual terminal (which usually "lives at" CTRL+ALT+F9).

But -- how can I also start a session that runs the traditional X-windows system?

- What do I need to install?

- How would I start a basic X-windows session?

My objective is to explore X the same way I have KDE.  As a supplemental virtual terminal to my "work doing" Gnome partition / terminal.  Any guidance in this regard will be happily received...

Cheers & thanks,
Ric
SFO

---

### Post by tyggna1 on 2008-02-10
xstart works pretty well for that.  If you have a package that manages services, you can also try:
servrice xserver start

---

### Post by Phrawm48 on 2008-02-10
> **tyggna1 said:**
> xstart works pretty well for that.  If you have a package that manages services, you can also try:
servrice xserver start

Thanks for your reply.[LIST]
[*]*xstart* I don't find at all, including in Synaptic.  *startx* I have and am using ala *startx**** -- :****1* to start the Gnome GUI login screen from which I can then choose either a Gnome or KDE desktop instance...
[*]Neither the  *service* nor *services* commands seem to be installed or installable...[/LIST]It seems to me, in my near-total ignorance, that I still need to both:[LIST]
[*]Download and install something
[*]Learn how to run that something from the command line of a virtual terminal[/LIST]Does anyone please have a bit clearer guidance for how I can install, configure, and run a "classic X" windows system in a virtual terminal?

Cheers & thanks,
Ric
SFO

---

### Post by Phrawm48 on 2008-02-18
Okay, I 've sorted this out.

What I was looking at / thinking of was Motif.

So there's not Motif desktop environment per se.  Instead, one or more desktop managers may use the Motif theme.

Live and learn,
Ric
SFO

---

