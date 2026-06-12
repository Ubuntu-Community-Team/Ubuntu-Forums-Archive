---
title: "Taking precautions before using the Restricted Drivers Manager"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by DavidJE13 on 2007-05-12
Hi, I've just upgraded to 7.04 (fresh install) and it's all installed (fairly) nicely so far, but no 3D acceleration (as usual). I have an ATI card.

[background - read if bored]
So, this Restricted Drivers thing looks good, and seems to be what to use to get hardware acceleration working. It lists "ATI accelerated graphics driver" turned off. So turn it on? I tried when I had just finished installing, and it broke the GUI something horrid (login screen worked, everything else was a block of colour). Instead of trying to fix this, I just re-installed Ubuntu again and problem solved. Thing is, this time I've done a lot of other things which I'd rather not have to go through again (just don't get me started on wireless network cards) so I'm taking precautions.

[the question]
What (if any) precautions can I take before enabling the restricted ATI driver, and what should I do to fix it if it does break the GUI again?
Also, is there another (better) way of getting 3D acceleration on an ATI card?

I'd rather have all the answers (or at least most of them) before I start.

---

### Post by Nikron on 2007-05-12
Well...  I doubt flipping it will result in you losing a GUI.  But, if you do lose your GUI does just change the /etc/X11/xorg.conf with nano.  Go down the the where it says 'Section "Device"' and change the driver to vesa or ati.  In any case, you probably wont have a problem.

---

### Post by mejy on 2007-05-12
Building on Nikron's answer, run 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak' in the terminal before installing the drivers and run 'sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf' if things go wrong.

---

### Post by DavidJE13 on 2007-05-12
"Well... I doubt flipping it will result in you losing a GUI."

um, well it did :P (read the boring background bit for details on that)

ok, so backing up this file is all it takes then? I thought there would be more to it than that. thanks for the replies. :)

I'll try it now and see how it goes *fingers crossed this time*

---

### Post by DavidJE13 on 2007-05-12
:(

it broke it again and I was left staring at a lovely beige colour. Still, at least this time I was able to fix it by just copying the file back (thanks for the tips)

So, does anyone have any idea *why* it's breaking so badly?

Edit:
or should I start this question in a new post?

---

### Post by mejy on 2007-05-13
Hmm... it's an ATI card.  To be honest, they're Linux support is currently worse than awful.  There could be any number of reasons why it isn't working for you, but we'll have a better chance of guessing if you post the model of your graphics card.  If at all possible, I'd recommend switching to a cheap nVidia card, since they provide far better operation under Linux (think faster, less resource heavy Beryl, multiple X servers, devent driver acceleration, a decent configuration front end, support for multiple graphics cards, better dual had support).

---

