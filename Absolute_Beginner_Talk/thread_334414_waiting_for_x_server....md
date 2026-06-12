---
title: "waiting for x server..."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by crispy_420 on 2007-01-08
First of all I'd like to say I don't know what I last did to screw up my login. I think I may have installed a bad theme for gdm, maybe. But now on to my problem.

When I tried to boot into Ubuntu today my xserver was screwed up. So I did what I always do, reconfigure to vesa drivers and try to solve my problem in a gui way (sorry I'm not a big fan of the command line). Still no luck.

I tried startx and it came down to this error:

[PHP]waiting for x server to shutdown FreeFontPath: FPE "/usr/share/X11/fonts/misc"
refcount is 2, should be 1: fixing[/PHP]

Is their anyway to repair and what did I do?

On a side note I also tried kdm, similar results there too. And even when I did manage to gdm up, it was a simple login that would not allow me to input anything. I think it maybe a font issue, but then again I did get to this point so I'm that bright.

Thanks

---

### Post by scrooge_74 on 2007-01-08
I no expert, but do you have a live CD on hand?

Boot from there, then mount your drive backup four xorg.conf file (even if it is no good) and copy in its place the one that the live CD is using

Maybe someone will have a more elegant solution

---

### Post by crispy_420 on 2007-01-09
I'll give it a try. But all I could find was a disc for LinuxMint, a heavily modified version of Ubuntu. At this point what more could I hurt right?

---

### Post by crispy_420 on 2007-01-09
Ok that did not work. But thanks anyway.

When I now boot I get two different errors:

1st

> **The greeter theme is corrupt**

The theme does not contain definition for the 
username/password entry element

2nd:

> [B]There was an error loading the theme,and the default theme 
could not be loaded. Attempting to start the standard greeter.[/B]

Now I end up with a default greeter that does not let me input username/password.

Looks to me like a bad greeter. How do I replace and go back to default greeter? Is that possible?

---

### Post by scrooge_74 on 2007-01-09
Try booting in recovery mode so you can select another GDM theme, this is something I have not yet manage to do to myself :D

---

### Post by crispy_420 on 2007-01-09
OK I solved my problem.

Here is how I did it to the best of my memory.

1. After failed login got to command line (Ctrl + Alt + F1). I guess recovery mode be the same.

2. startxfce4 to get to a gui (xfce)

3. started synaptic to completely remove gdm & kdm (wanted complete removal with all config files) - this also took ubuntu-gnome with it

4. reinstalled gdm & ubuntu-gnome

Everything works fine but it seems I lost setup of a few things. That is no big deal, infact I expected it. I just have to setup the side buttons on my logitech mouse again but I think I'll survive.

But if someone knows a better fix for this issue, please correct me. I know this stressed me pretty bad and I was fearing a reinstall from scratch (after I recovered as much data as possible).

How do I go about marking this "solved"?

---

### Post by scrooge_74 on 2007-01-09
There should be a link on the page for you to click

---

