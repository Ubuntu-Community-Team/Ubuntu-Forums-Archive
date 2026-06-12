---
title: "Optimizing Desktop for Speed?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by ekdysiast on 2007-03-12
I've been rummaging around the system settings for a while, and I can't find a way to optimize my desktop appearance for speed.

For example, when I use XP, I go to "my computer > properties > advanced >..." And simply click on "optimize for speed" and all the bells and whistles are gone.

With Ubuntu, some of the features I don't need are:
[LIST=1]
[*]being able to view a window's contents while I'm moving it around
[*]having a fancy black box minimizing to the corner when I click minimize
[*]And possibly many more that I haven't encountered yet
[/LIST]

Anyway, help would be appreciated.

---

### Post by buuntuu! on 2007-03-12
looks as if you were looking for an alternative window-manager.
if you like simplicity and speed (and are not afraid of a somewhat commandline-like approach) openbox will blow you away!
if you like simplicity and (a little less) speed and an experience close to the desktops you know, try fluxbox.
they are both in the repositories...

---

### Post by Bachstelze on 2007-03-12
Do you want "apparence" or "speed" ? Both are mutually exclusive if you don't have a strong graphics card. If you have one, you can do things like [that](http://img441.imageshack.us/img441/9/kdecompositech0.png) with very little tweaking - assuming you're runing KDE :)

---

### Post by ekdysiast on 2007-03-12
I don't care if it's butt ugly as long as there's no sensation of "lag". My graphic card's the type that comes on your Main Board, and all I want Ubuntu for is to do some programming over an ssh connection in an X window environment. Maybe I'll try out openbox (does it support GTK, though?).

---

### Post by buuntuu! on 2007-03-12
openbox is far from ugly, it's just reduced to what you NEED!
there isn't even a panel by default (easy to install though)
see this thread for a little [howto]("http://ubuntuforums.org/showthread.php?t=192106") on installing and setting up
gtk is supported, 
you'll love it

---

### Post by Songwind on 2007-03-12
This doesn't answer your question directly, but it is something I found on my own system.

Make sure you aren't running any unnecessary services.  If you don't even own a type of hardware, disable support for it, that sort of thing.  It will shrink your memory footprint and free up a few CPU cycles.

---

### Post by ekdysiast on 2007-03-12
Before I try openbox (since I'm rather unfamiliar with the linux environment), Songwind, could you throw me a few links to good guides for service optimization in Ubuntu?

Appreciate it.

---

### Post by Crakie on 2007-03-12
Apart from Openbox, there are several other WM or desktop environments that are optimized for speed. Among them are Fluxbox, IceWM, XFCE. A little googling will get you a long way, although trying them is probably the only way to see how things work out speedwise.

If you are really a speedfreak, then you should look into compiling your own kernel, leaving out unnecessary stuff, and tweaking your modules.

---

### Post by arron on 2007-03-12
Not sure why this didnt come up, but try the Xubuntu desktop, its lighter & faster.  As well the  Fluxbox or Blackbox are nice light fast wm's.

---

### Post by penp on 2007-03-12
> **arron said:**
> Not sure why this didnt come up, but try the Xubuntu desktop, its lighter & faster.  As well the  Fluxbox or Blackbox are nice light fast wm's.

Xubuntu is simply a distro of Ubuntu which uses the XFCE window manager (much like Kubuntu is a distro of Ubuntu which has KDE pre-installed). When I was running debian, I tried both fluxbox and XFCE. I liked the utter customizability of fluxbox, but XFCE was a little more user friendly. Both were considerably more lightweight than Gnome.

---

### Post by Songwind on 2007-03-12
> **ekdysiast said:**
> Before I try openbox (since I'm rather unfamiliar with the linux environment), Songwind, could you throw me a few links to good guides for service optimization in Ubuntu?

Appreciate it.

I'd love to, but I didn't use any guides. :P

I just went through the list and thought about whether or not I was using each components.  "I don't own any bluetooth devices, time to get rid of that."  That sort of thing.  I hate text-to-speech so I uninstalled all those components, etc.

Some things will get you a smaller memory footprint but others will just get you more disk space.  Depends entirely on what you have running vs. what is only installed.

---

### Post by igknighted on 2007-03-12
Xfce is really only significantly faster than gnome/KDE when you give up high memory apps.  Things like OpenOffice.org and Firefox should be replaced (try abiword/gnumeric and epiphany) because they eat system resources quickly.  I can run gnome, or especially KDE if I am careful with what I have running.  In fact, KDE has a wizard on the first run that lets you turn fancy stuff off.  Doing this and running all KDE apps provides a very quick desktop that is right there with Xfce.

I love fluxbox and IceWM as well.  Look at bodhi.zazen's sig for some how to's on these WM's

---

### Post by arron on 2007-03-12
> **penp said:**
> Xubuntu is simply a distro of Ubuntu which uses the XFCE window manager (much like Kubuntu is a distro of Ubuntu which has KDE pre-installed). When I was running debian, I tried both fluxbox and XFCE. I liked the utter customizability of fluxbox, but XFCE was a little more user friendly. Both were considerably more lightweight than Gnome.

You can have both xubuntu and ubuntu on the same install, and switch the desktop.  you can install the xubuntu desktop with:

sudo apt-get install xubuntu-desktop 

and have all the xubuntu apps and setup without reinstalling everything. this takes some space, but can be removed if so wished as in here:

[http://www.ubuntuforums.org/showthread.php?t=358828](http://www.ubuntuforums.org/showthread.php?t=358828)

---

### Post by picpak on 2007-03-12
Here's a guide to disable unneeded services:

[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

---

### Post by ekdysiast on 2007-03-12
Thanks, everyone, for the helpful advice.

Now it's time for me to do some tweaking.

---

### Post by buuntuu! on 2007-03-13
> **igknighted said:**
> Xfce is really only significantly faster than gnome/KDE when you give up high memory apps.  Things like OpenOffice.org and Firefox should be replaced (try abiword/gnumeric and epiphany) 
 i agree. i tried gnome kde and xfce and was not really impressed by xfces speed (with the standard install) openbox however lets me run my favourite apps significantly faster without twearking around.

---

### Post by wj32 on 2007-03-13
Open up gconf-editor:

1. goto /apps/metacity/general/ and check reduced_resources
2. disable previews in nautilus
3. other stuff...

---

