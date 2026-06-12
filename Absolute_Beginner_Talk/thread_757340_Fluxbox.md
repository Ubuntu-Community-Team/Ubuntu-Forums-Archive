---
title: "Fluxbox"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-16
How do you install flux box to coexist with gnome?

---

### Post by Crafty Kisses on 2008-04-16
Not sure what your asking, but you can install Fluxbox by doing:
```
sudo apt-get install fluxbox
```
Then you can enter Fluxbox by pressing:
```
Ctrl+Alt+Backspace
```
Then go to "Select Session" and mark Fluxbox.

This link may help you: [http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)

---

### Post by hikujk123 on 2008-04-16
Is this the best way to install it?  I have heard you should use aptitude. I don't mean use them at the same time.  I mean so that I can select it under the session menu.  Please respond.

---

### Post by Promaster91 on 2008-04-16
No I installed it using sudo apt-get install fluxbox. Or you can use you Synaptic Package Manger,

---

### Post by hikujk123 on 2008-04-16
How do you uninstall it then?  I was told that with other desktop environments you use aptitude because it makes it easier to get rid of.

---

### Post by Meskarune on 2008-04-16
doing apt-get is pretty much the same thing. Don't worry about it. Its fine.   :)

And Fluxbox already uses gnome to theme its windows...so I think you are over thinking things. 

Ubuntu uses compiz with gnome. Xubuntu uses xfce with gnome. 

Gnome works well with others.

---

### Post by Crafty Kisses on 2008-04-16
> **hikujk123 said:**
> How do you uninstall it then?  I was told that with other desktop environments you use aptitude because it makes it easier to get rid of.

```
 sudo apt-get remove fluxbox
```

---

### Post by Triggerhapp on 2008-04-16
> **Meskarune said:**
> doing apt-get is pretty much the same thing. Don't worry about it. Its fine.   :)

And Fluxbox already uses gnome to theme its windows...so I think you are over thinking things. 

Ubuntu uses compiz with gnome. Xubuntu uses xfce with gnome. 

Gnome works well with others.
Actually XFCE and Gnome dont co-operate :) Just the Gnome-based programs. XFCE has KDE and Gnome support, meaning it tries to play well with programs made in GTK+ and QT, but other than that, its nothing to do with Gnome :)

---

### Post by Meskarune on 2008-04-16
```
apt-get --purge remove fluxbox
```

Not hard at all. Where are you getting your information?

---

### Post by Meskarune on 2008-04-16
> **Triggerhapp said:**
> Actually XFCE and Gnome dont co-operate :) Just the Gnome-based programs. XFCE has KDE and Gnome support, meaning it tries to play well with programs made in GTK+ and QT, but other than that, its nothing to do with Gnome :)

Heh. As a rule I don't really use KDE anything. And I concede the point. But alot of new users don't understant the difference between a window manager and a desktop enviroment. I was trying to keep things simple. :)

---

### Post by Triggerhapp on 2008-04-16
> **Meskarune said:**
> Heh. As a rule I don't really use KDE anything. And I concede the point. But alot of new users don't understant the difference between a window manager and a desktop enviroment. I was trying to keep things simple. :)

Ah, my bad then, sorry im pedantic XD
Ive only ever looked at KDE once over, gave it a go thinking "It cant be that bad .... right?" wrong.
Stuck to Amarok for a while except that loading GTK and QT doesnt play nice with my limited (lol?) 1Gig memory.
More on topic, I've tried a few *boxes and found that while VERY functional, it left me wanting. I like my eyecandy XD

on topic : Aptitude, apt-get and synaptic, in Ubuntu, all work on the EXACT same "dpkg" system. Any or all could be used to install and remove programs safely on Ubuntu

---

### Post by hikujk123 on 2008-04-16
I installed Fluxbox, but there was only a blue screen, a bare minimum panel, and no way to select any applications.  I only had a clock and it was the only thing I could adjust.  PLEASE HELP.  I want a light windows manager/desktop environment (no, don't know the difference).

---

### Post by Triggerhapp on 2008-04-16
Explain a little better what you were after? :)

Did you want Gnomes Panels and desktop, while using less resources?

---

### Post by Promaster91 on 2008-04-16
```

 sudo apt-get remove fluxbox

```
From what I heard, there is no big difference between apt-get and aptitude.

---

### Post by hikujk123 on 2008-04-16
I was have tried kde, xfce, and gnome.  I like them but they use too many resources.  Enlightenment was just too ugly.  I heard of fluxbuntu and looked up screen shots and it was beautiful, but I don't was to switch distros no matter how closely related.  I thought fluxbox would at least have as many options as enlightenment.  Why can't I choose any applications?

---

### Post by Meskarune on 2008-04-16
> **hikujk123 said:**
> I installed Fluxbox, but there was only a blue screen, a bare minimum panel, and no way to select any applications.  I only had a clock and it was the only thing I could adjust.  PLEASE HELP.  I want a light windows manager/desktop environment (no, don't know the difference).

That is how fluxbox looks. Have you tried using the rightclick menu? You can configure some things from there. Also, you could open a terminal and type the name of any program or your filer to run it. Fluxbox is edited by text files in the .fluxbox directory. You would learn a lot more about using fluxbox at their site though. 

Flux is one of my favorite window managers. But you do have to use the command line with it.

---

### Post by Triggerhapp on 2008-04-16
to get to your programs, i beleive you have to right-click the desktop, to get a menu.
If this is empty, you need to Create this menu first, although I thought they automagically created these on install... try that, let me know

---

### Post by hikujk123 on 2008-04-16
WHen I right click, nothing shows up!

---

### Post by hikujk123 on 2008-04-16
Does anyone know of a light more user-friendly manger?  What is IceBuntu?  I would like to stay with ubuntu just install a new desktop environment.

---

### Post by Triggerhapp on 2008-04-16
I would advise, personally, IceWM ```
sudo apt-get install icewm
``` I love this myself, its very quick and can be set up to look like Windows, if you like that kinda thing, or set up to have a scheme that looks drug-enduced... I shall have to find the name of that one for you :P

---

### Post by Monsuco on 2008-04-16
You may want to also install fbdesk (or something like that). It lets fluxbox have desktop icons. Using synaptic (or Adapt) you might find some other FB stuff. There is a version of Ubuntu called [Fluxbuntu](http://fluxbuntu.org/) built to integrate well with Fluxbox.

As for lightweight and easy, there is [Xubuntu](www.xubuntu.org) which is officially maintained by Canoical (don't confuse it with xUbuntu, the xbox version). [Ubuntu Lite](http://ubuntulite.tuxfamily.org/) is another lightweight. There is the [IceBuntu](https://wiki.ubuntu.com/IceBuntu) theme for IceWM, a light window manager. [url=http://dev.thinkgos.com/]gOS uses the odd, configurable, and light enlightenment.

You can also turn off stuff in gnome/KDE that you don't use.

---

### Post by Meskarune on 2008-04-16
you could also try window maker. Its more feature rich than fluxbox, but still minimalist. 
[http://www.windowmaker.info/gallery.php](http://www.windowmaker.info/gallery.php)

---

### Post by jviscosi on 2008-04-17
> **Meskarune said:**
> you could also try window maker. Its more feature rich than fluxbox, but still minimalist. 
[http://www.windowmaker.info/gallery.php](http://www.windowmaker.info/gallery.php)

Window Maker could indeed be a better choice than Fluxbox if you want something with more GUI applications for configuration options.  It's also faster than Fluxbox, at least on my machine.  I'm considering going back to it from Fluxbox, actually, but can't quite give up the Fluxbox window "remember yada yada" options ...

You could also look at OpenBox, which like WindowMaker has more default GUIs for configuring it than Fluxbox does.

For a good rundown on how to set up Fluxbox, see Red Squirrel's excellent post [here]("http://ubuntuforums.org/showthread.php?t=371144").

---

### Post by herbster on 2008-04-17
Hikujk, to create your fluxbox menu if you have none on your first login, go back into Gnome and open a terminal, enter this:

```
sudo update-menus
```

When done, log out and log back in to fluxbox. Right-click on the desktop and you should have your menu.

To use a window manager, you will typically need to configure everything yourself. This is done in specific files, with fluxbox they are:

~/.fluxbox/startup -> All settings related to what happens once you log in to your fluxbox session. Which programs automatically run, your wallpaper, daemons, etc. (Similar to System > Preferences > Startup/Sessions in Gnome).
~/.fluxbox/keys -> All your keyboard/mouse shortcuts.
~/.fluxbox/menu -> Your right-click menu, where you can change how it appears, which programs are listed, etc.

I've been using fluxbox for a long time now, it's my favourite window manager by miles, so hopefully we can help you get the most out of it. Keep asking, but also read the documentation at fluxbox.sourceforge.net/docs/ and jviscosi's link above is excellent for the brand new.

---

### Post by eriqjaffe on 2008-04-17
> **herbster said:**
> ~/.fluxbox/menu -> Your right-click menu, where you can change how it appears, which programs are listed, etc.

Be aware that you'll have to manually add newly installed programs to the fluxbox menu, it doesn't auto-update.  There's a program out there called [marchfluxmenu]("http://code.google.com/p/marchfluxmenu/") that will assist with auto-updating the menu...it's not in the repos (so you can't install it via aptitude/apt-get/synaptic), and you'd have to compile it from source yourself.  But it works.

---

### Post by linuxlizard on 2008-04-17
just get fluxbuntu and try it out. It's already set up.

If you are seriously needing lightweight- pcfluxboxos can't be beaten IMO. I've got it running great on as low as a 333mhz with 128 mb ram, and it flies on my p3 700mhz laptop with 192 mb ram.

Fluxbox has to have a .menu file in the home directory which is edited as you add programs. This may be why you don't see anything but the clock when you install it in ubuntu. Also, it is lightweight- you click on the desktop to bring up the menu, there are no icons standard, no filemanager built in, etc. You have to add each piece yourself, or get fluxbuntu or pcfluxboxos which are already set up for you.

---

