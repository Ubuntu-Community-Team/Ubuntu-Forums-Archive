---
title: "How do I get multiple monitor support?"
date: 2008-10-29
forum: Apple Hardware Users
---

### Post by pidayman on 2008-10-29
Yes, I know this has been posted, like, a billion trillion quadrillion  times maybe, but my situation is very different from all the results I found from my searches.

My situation is this: I need multiple monitor support in order to use a projector with it. In other words, I don't want any big screen option, I need a Clone Screen option. I tried a method or two, and nothing worked.

Specs:
Apple PowerBook G3 Pismo (Firewire built-in) Laptop with a port for VGA, **not** DVI like most modern Apple computers. 500 MHz processor with an upgrade of RAM to 384 MB. 12 GB hard-drive. I had to modify the default xorg.conf configuration to get 1024x768 resolution to fill the screen, by the way.

I am running Ubuntu 8.04 (I think it's 8.04.1 LTS, but I'm not sure) with a plan to upgrade to 8.10 as soon as possible. Don't let this upgrade plan limit the solution, I can definitely do the steps over if they get reset during an upgrade.

---

### Post by garyedwardjohnston on 2008-10-29
Firstly, I would do a clean install instead of upgrades.  They are cleaner.

Next to your issue:

System > Screen Resolution > Clone Screens (make sure it's checked)

Nice and easy :)

---

### Post by pidayman on 2008-10-30
Last time I tried that, it had no effect on what was on the screen. Of course, I may not have had the monitor plugged in at the start and I know I didn't refresh X11 (the ctrl-alt-backspace keypress or something) after setting the option. I should try that again tomorrow, it's getting late here. I'll get back to you on this tomorrow, after I get a chance to try it again.

---

### Post by pidayman on 2008-11-02
It didn't work. I need a solution NOW. I'm sorry for the urgency, but I have to use this tomorrow for a presentation. I forgot to mention that my g3 pismo powerbook has an ATI Rage 128 video card. I really need to find a solution. I've tried editing my xorg.conf file for Xinerama, MergedFB, and nothing I've tried works!!! I'm at my wits end, and I need a solution before the end of the day! (for me that end is 11PM PST)

---

