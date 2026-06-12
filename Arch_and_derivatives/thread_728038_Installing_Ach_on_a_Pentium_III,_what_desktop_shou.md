---
title: "Installing Ach on a Pentium III, what desktop should I use?"
date: 2008-03-18
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-03-18
Pentium III @ 1Ghz;
512MB RAM @ 133Mhz.

I know that I meet the RAM requirements for any DE, but the processor and the RAM's speed aren't top of the line and I like my DE to be very snappy.

I really like XFCE, Gnome, and KDE almost equally, so it's very hard for me to decide. Plus I haven't seen or used KDEmod, which sounds pretty cool.

Also, unrelated: What other things should I do in Arch to speed up this computer?

---

### Post by MONODA on 2008-03-18
I would use xfce I use it for arch too even though my pc can easily handle gnome or kde.
EDIT: I just checked out KDEmod, it seems cool, maybe you should try that out instead.

---

### Post by kerry_s on 2008-03-18
> **EmosSuck777 said:**
> Pentium III @ 1Ghz;
512MB RAM @ 133Mhz.

I know that I meet the RAM requirements for any DE, but the processor and the RAM's speed aren't top of the line and I like my DE to be very snappy.

I really like XFCE, Gnome, and KDE almost equally, so it's very hard for me to decide. Plus I haven't seen or used KDEmod, which sounds pretty cool.

Also, unrelated: What other things should I do in Arch to speed up this computer?

yeah right, i wish i had those spec's. mines a measly 450mhz 256mb ram.

you can use 1 of the *box's, me i use jwm on debian etch/lenny custom install.
stick with gtk2 app's, programs that don't have much dependency's.

me, i use web app's where i can, cause my browser's pretty fast.
example: google for the office stuff, meebo.com for im.

my startup ram use is only 22mb, i rarely dip into swap, i have to do alot for it to use swap. rox is my file manager, leafpad for text or xedit comes with xorg, vlc for music and vids, mtpaint to mess with images, calculator i use xcalc since it comes with xorg, xterm comes with xorg, mc for console work.
pic

---

### Post by Sunflower1970 on 2008-03-18
I'm using XFCE on my Arch partition. It's a PII 400 Mhz 384MB Ram. Runs quite smoothly. (Even have either desktop effects or Compiz running quite smoothly too.)

---

### Post by Pogeymanz on 2008-03-18
I'm guessing I'll do XFCE, as I usually do. :)

I don't need it to be super-minimal light-speed. I just want to make sure it's as fast as it was when I did a fresh install of Win98, back when it was relatively new and had only 128MB RAM.

---

### Post by Rumor on 2008-03-18
I have a machine similar to that spec . . . P3/700 with 512 ram. It will run Gnome just fine, but Fluxbox is very, VERY snappy.

---

### Post by finferflu on 2008-03-18
One suggestion is to use even big DEs such as Gnome or KDE, but avoid using things like conky and other such apps that are quite resource-demanding, crawling in the background (and useless! but that's just my point of view :P).

---

### Post by kerry_s on 2008-03-18
> **finferflu said:**
> One suggestion is to use even big DEs such as Gnome or KDE, but avoid using things like conky and other such apps that are quite resource-demanding, crawling in the background (and useless! but that's just my point of view :P).

conky is low resource 0.92mem & 0.40cpu(on mine), yet gives alot of info, mine's set to run every 2.5sec's in the conkyrc.

---

### Post by mips on 2008-03-18
You have got 512MB of ram, go KDEmod and only install what you need. You will be pleasantly suprised is all I can say.

---

### Post by finferflu on 2008-03-18
Yeah, perhaps I was too imprecise. I meant that running those background scripts to check system info is very resource-hungry. That of course doesn't apply to the conky built-in commands. Shell scripts and things of this sort can be a huge hog. Back when I was on Xmonad, I used to run a Shell script to monitor my volume, running every 1 or 2 seconds: the system felt a lot heavier.

---

### Post by kerry_s on 2008-03-18
> **finferflu said:**
> Yeah, perhaps I was too imprecise. I meant that running those background scripts to check system info is very resource-hungry. That of course doesn't apply to the conky built-in commands. Shell scripts and things of this sort can be a huge hog. Back when I was on Xmonad, I used to run a Shell script to monitor my volume, running every 1 or 2 seconds: the system felt a lot heavier.

yeah, i got that, just depends on how you use it, what you want to keep track of. i find it easy to see what's happing at a glance, instead of opening a terminal and running the various commands.
most people don't actually need to keep a watch on things anyway, 90% of the time it's covered by programs anyhow. :lolflag:

it's also the only thing i run to break up the black, i don't use a background i prefer to use that extra 8mb of ram for programs instead of drawing a background.

---

### Post by K.Mandla on 2008-03-18
Welcome to the party.

[http://kmandla.wordpress.com/hardware#Inspiron](http://kmandla.wordpress.com/hardware#Inspiron)

Runs Arch almost 24-7, although I have been known to float beyond Arch into other distros with it. :D

---

### Post by MisfitI38 on 2008-03-18
I have a Thinkpad with identical specs. It runs KDE, GNOME, and Xfce very, very well. Slight edge goes to Xfce in responsiveness. Fluxbox, of course, is even snappier.

---

### Post by Pogeymanz on 2008-03-19
K.Mandla: What DE do you use on that Inpsiron?

I still can't decide...

I guess I'm struggling between XFCE and KDEmod. Gnome isn't different enough from XFCE to warrant running it on an older machine, IMO.

I'm wondering: Is there anyway to install KDEmod and then remove EVERYTHING that came with it if I don't like it? As far as I know, there isn't; I'd still have Kate and Kopete, etc. I don't want to have to find every app that came with it and remove it manually. That's the only reason I wont just install both and see which one I like best.

---

### Post by mips on 2008-03-19
pacman -Rcs kdemod-complete kdemod-kde-l10n-$YOUR_LOCALIZATION

might do it, not to sure though

---

### Post by MisfitI38 on 2008-03-19
From KDEMod faq:

Q: How can i uninstall/remove KDEmod?

A: All our packages are prefixed with kdemod-, so just do pacman -Q | grep kdemod and remove all results with pacman -Rd package. Then remove qt3-enhanced and KDEmod should be removed completely... Another way to remove it is to run pacman -Rd kdemod-complete

---

### Post by RedSquirrel on 2008-03-19
You might want to look at Openbox as well. It's my current favourite.

You can use it on its own or as the window manager for Xfce.

---

### Post by desper on 2008-03-20
Openbox is a real light one, and also a powerful one.
The keybinding and menu is enough for me to do any daily taks, more speed and more efficiency. Actually I am so glad  that I could get t rid of mouse, panel, desktop icon, all these things and their time-consuming problems.  The only cost is that I spent an afternoon learning openbox wiki and tweaking the conf file. 
Best desktop is no desktop at all.

---

### Post by aeto on 2008-03-20
I used to run KDE/GNOME and Compiz perfectly fine on the following:

Pentium 866
256MB
FX5200

It seems people have forgotten how sturdy good old hardware were, taking the crap quality of today's manufacturing as the epitome of good performance.

---

### Post by canistra on 2008-03-21
Just use openbox!

---

### Post by cardinals_fan on 2008-03-22
Xfce is awesome, but nothing beats the *boxes for speed.

---

### Post by K.Mandla on 2008-03-22
> **canistra said:**
> Just use openbox!
> **cardinals_fan said:**
> Xfce is awesome, but nothing beats the *boxes for speed.
+1x2!

---

### Post by LookTJ on 2008-03-23
For a good start out, I suggest OpenBox as the window manager and your choice of DE(I recommend XFCE, though I use GNOME)

---

### Post by Pogeymanz on 2008-03-23
I've pretty much decided on XFCE, but is openbox really so good that I should use it with XFCE? It seems like all Arch users are using openbox! I have to at least try it out on my laptop later.

---

### Post by MisfitI38 on 2008-03-23
> **EmosSuck777 said:**
> I've pretty much decided on XFCE, but is openbox really so good that I should use it with XFCE? It seems like all Arch users are using openbox! I have to at least try it out on my laptop later.

Openbox is nice and light. It requires a lot of configuration, but is customizable down to the very last detail.
It is not for everyone, though.
ROX works well as a file manager for it, and adds icons, drag and drop, etc.
I recently added a brief howto to the openbox wiki page, for using openbox as the wm for Xfce4, if you're interested in that.
You can also run openbox as your wm, and simply start xfce4-panel afterward, for a more hybrid-approach.
Like I said, the customization and combinations are endless... ;)

---

### Post by LookTJ on 2008-03-23
> **Taylor said:**
> For a good start out, I suggest OpenBox as the window manager and your choice of DE(I recommend XFCE, though I use GNOME)I forgot to mention, to edit openbox, install obconf(gui)

---

