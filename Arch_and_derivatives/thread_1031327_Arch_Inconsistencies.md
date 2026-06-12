---
title: "Arch Inconsistencies"
date: 2009-01-05
forum: Arch and derivatives
---

### Post by Open-SuSe-A-Me on 2009-01-05
Hello let me first say that I've been using Arch for about a week and I love it.  I dont think I can ever use another distro, it just wouldnt feel right, but a there are a couple of things i'd like to adjust/fix:

1.  I ditched KDE3 for Gnome (once i remembered how much better Gnome is).  About 30% of the time when i log into Gnome my GTK theme doesnt appear and it defaults to some hideous 1990's plain looking theme (not the default clearlooks or the dark theme I use).  Is this a known bug/issue?  I couldn't find anything on google.

2.  Exaile keeps freezing (seemingly at random) and the terminal displays a "Database Locked" error.  Not sure if this is an Arch issue, but Exaile worked beautifully in Ubuntu Hardy with all the same settings/songs.  Upon googling i discovered that this is a known problem, but i couldn't find a fix anywhere.

3.  I had to patch my Intel 965 video card to force it to use overlay video (you can see what i did here > [http://ubuntuforums.org/showthread.php?t=1025340&page=3](http://ubuntuforums.org/showthread.php?t=1025340&page=3)  which worked and my videos didnt tear anymore, but using this patch causes my screen to flicker when a video is opened and about 20% of the time the screen will turn one (random) color and i will have to force a hard reboot.  There is a bug on launchpad about this, but my question is: is there anyway to "revert" my Intel driver to whatever version is included in Hardy?  That version works great.

Thanks! I'm glad I found this distro.

---

### Post by crimesaucer on 2009-01-05
> **Open-SuSe-A-Me said:**
> Hello let me first say that I've been using Arch for about a week and I love it.  I dont think I can ever use another distro, it just wouldnt feel right, but a there are a couple of things i'd like to adjust/fix:

1.  I ditched KDE3 for Gnome (once i remembered how much better Gnome is).  About 30% of the time when i log into Gnome my GTK theme doesnt appear and it defaults to some hideous 1990's plain looking theme (not the default clearlooks or the dark theme I use).  Is this a known bug/issue?  I couldn't find anything on google.

2.  Exaile keeps freezing (seemingly at random) and the terminal displays a "Database Locked" error.  Not sure if this is an Arch issue, but Exaile worked beautifully in Ubuntu Hardy with all the same settings/songs.  Upon googling i discovered that this is a known problem, but i couldn't find a fix anywhere.

3.  I had to patch my Intel 965 video card to force it to use overlay video (you can see what i did here > [http://ubuntuforums.org/showthread.php?t=1025340&page=3](http://ubuntuforums.org/showthread.php?t=1025340&page=3)  which worked and my videos didnt tear anymore, but using this patch causes my screen to flicker when a video is opened and about 20% of the time the screen will turn one (random) color and i will have to force a hard reboot.  There is a bug on launchpad about this, but my question is: is there anyway to "revert" my Intel driver to whatever version is included in Hardy?  That version works great.

Thanks! I'm glad I found this distro.

For #1, it could be the gtk theme that you are using has some sort of mis-written part in it.


The ugly interface is what it looks like when you don't use a gtk engine like clearlooks or murrine. If a theme is written incorrectly it will show like that because it won't be able to use the engine it is written for. 


So try a different gtk theme to see if it keeps breaking like that (try something like clearlooks-glossy or clearlooks).....

---

### Post by RiceMonster on 2009-01-06
If your gtk theme was working before you logged in, but didn't this time, hit alt f2 and type
```
gnome-settings-daemon
```

---

### Post by Open-SuSe-A-Me on 2009-01-06
Ok thanks for the replies.  I just noticed that in the appearences prefs it says "this theme will not look as intended because the required gtk+ engine is not installed" but it does not say what engine and i installed a bunch of them already as mentioned in the Gnome Arch wiki.  And when the theme does load it works perfectly.  I dont get it.

Any ideas about #2 and #3?

Thanks so much.

---

### Post by crimesaucer on 2009-01-06
> **Open-SuSe-A-Me said:**
> Ok thanks for the replies.  I just noticed that in the appearences prefs it says "this theme will not look as intended because the required gtk+ engine is not installed" but it does not say what engine and i installed a bunch of them already as mentioned in the Gnome Arch wiki.  And when the theme does load it works perfectly.  I dont get it.

Any ideas about #2 and #3?

Thanks so much.

Look at the directory where the theme is. Either you have put it in ~/.themes or /usr/share/themes.... in either of those 2 directories is the folder with the name of your theme.... we'll call it "broken-theme".

So in /"broken-theme"/gtk-2.0/gtkrc:

Read the gtkrc file. Look for the part that says, style "theme-default". It will be written at the bottom of that top "style" section as:


engine "xfce" 

or:

engine "murrine" 

or: 

engine "clearlooks"



That is your gtk theme engine for that theme. Make sure you have it installed, and make sure the theme is written properly for it.


.... or you could always find a new theme at gnome-looks.org.

---

### Post by kpkeerthi on 2009-01-07
1. Delete (or 'move' to a temp folder) the contents of ~/.config/autostart and reboot. This will reset the default startup helpers programs (daemons and such) required for GNOME. You may then add your on top of from System -> Preference -> Session -> Autostart.

2. I have been running Exaile without lockups in Arch. So definitely not an Arch issue. My music library has about 8000 files. Try deleting  Exaile's database file build it again.

---

### Post by Open-SuSe-A-Me on 2009-01-07
> **crimesaucer said:**
> 

Read the gtkrc file. Look for the part that says, style "theme-default". It will be written at the bottom of that top "style" section as:


engine "xfce" 

or:

engine "murrine" 

or: 

engine "clearlooks"



That is your gtk theme engine for that theme. Make sure you have it installed, and make sure the theme is written properly for it.

All i could find was the word "pixmap", but RiceMonsters' suggestion works when it does not load.

@kpkeerthi
I uninstalled Exaile and deleted /.exaile, reinstalled, and now its working great, thanks!

Anyone have any idea about my video driver?  If i can use an older version?

---

### Post by fwojciec on 2009-01-07
> **Open-SuSe-A-Me said:**
> All i could find was the word "pixmap", but RiceMonsters' suggestion works when it does not load.

Maybe you need the pixmap engine installed?  It's a part of "gtk1-engines" package.

> **Open-SuSe-A-Me said:**
> Anyone have any idea about my video driver?  If i can use an older version?

No idea -- you can always try building your own version of the driver you want.  It is possible that the old driver will not work with the new version of xorg, though.  You won't know until you try.

In principle -- I think that using old versions of packages in Arch is not a very good long-term solution.  Sooner or later you'll run into compatibility problems, since the rest of the system is updated constantly.  A better solution is always to try and find/help create a fix for the current version.

---

### Post by Open-SuSe-A-Me on 2009-01-07
> **fwojciec said:**
> Maybe you need the pixmap engine installed?  It's a part of "gtk1-engines" package.



No idea -- you can always try building your own version of the driver you want.  It is possible that the old driver will not work with the new version of xorg, though.  You won't know until you try.

In principle -- I think that using old versions of packages in Arch is not a very good long-term solution.  Sooner or later you'll run into compatibility problems, since the rest of the system is updated constantly.  A better solution is always to try and find/help create a fix for the current version.

I did not have the "gtk1-engines" installed, thanks.

About the driver, the reason i would like to try the old one is because i either have awful tearing in my videos or I risk the whole system freezing.  The driver that is used on Hardy works flawlessly so there must be some way to fix it.  I guess i could wait for a new driver version to come out, but who knows when that will happen.

---

### Post by chucky chuckaluck on 2009-01-09
**gtk-chtheme** is a theme switcher that affects the .gtkrc-2.0 file, allowing you to switch both gtk theme and font (icon theme still has to be changed in the .gtkrc.mine file). it's a lighter weight alternative to gnome-settings-daemon and all its gnome dependencies.

---

### Post by K.Mandla on 2009-01-09
> **chucky chuckaluck said:**
> **gtk-chtheme** is a theme switcher that affects the .gtkrc-2.0 file, allowing you to switch both gtk theme and font (icon theme still has to be changed in the .gtkrc.mine file). it's a lighter weight alternative to gnome-settings-daemon and all its gnome dependencies.
+1. It's awesome.

---

### Post by SomeGuyDude on 2009-01-10
> **chucky chuckaluck said:**
> **gtk-chtheme** is a theme switcher that affects the .gtkrc-2.0 file, allowing you to switch both gtk theme and font (icon theme still has to be changed in the .gtkrc.mine file). it's a lighter weight alternative to gnome-settings-daemon and all its gnome dependencies.

LXAppearance takes care of gtk/font/icons seamlessly.

---

### Post by kerry_s on 2009-01-10
> **SomeGuyDude said:**
> LXAppearance takes care of gtk/font/icons seamlessly.

+1 its a much better gui.

---

### Post by K.Mandla on 2009-01-10
Interesting; LXAppearance always used to scramble the GTK and icon themes so I had to pick them out of the same list. Maybe that's changed; I'll take another look at it.

---

### Post by kerry_s on 2009-01-10
> **K.Mandla said:**
> Interesting; LXAppearance always used to scramble the GTK and icon themes so I had to pick them out of the same list. Maybe that's changed; I'll take another look at it.

yeah, if it's been awhile the lx* stuff is worth another look, most of it is nice, but forget lxde desktop, it's still buggy as hell, mostly the panel it constantly wigged out on me and would just startup flashing in and out, usually just deleting ~/.config/lxpanel would fix it but you'd have to set it up all over again. lxterminal is a bit slow but very usable. pcmanfm is getting there and if you use the "pcmanfm -d" in your startup to run it as a daemon, it's pretty damn quick, it's like konqueror's preload setting in kde. anyway's i tried gnome, than lxde and now i'm on xfce4. it's a old ibm t20 700mhz 256mb ram(sometimes 128mb, 1 memory slot is going bad) so i'm just seeing what runs best, i'm basically just trying to get to know the laptop.

---

### Post by SomeGuyDude on 2009-01-10
LXDE as a whole was a great start, but now I'm just about the Openbox. That said, PCManFM is infinitely superior to any filemanager I've used, also LXTerminal is pretty damn good.

---

### Post by handy on 2009-01-10
I spent many years using the directory utility - DOpus, on the AmigaOS, so when I found Worker a while back I was stoked, as it shares many similarities with DOpus. 

Worker is incredibly configurable in many ways through the graphical configuration editor.  It also has many built in commands, yet you can also call other commands & run scripts from it.  There are multiple ways for the front end to display, it has multiple layers of buttons both for path & command (as many as you need) the command buttons can have a RMB command as well (the dog eared corner indicates RMB option is available - as seen in the screenshot below), it is fast, light, just needs the X libs.

It can do great deal more than I have need for.

---

### Post by chucky chuckaluck on 2009-01-11
> **SomeGuyDude said:**
> LXAppearance takes care of gtk/font/icons seamlessly.

well now, isn't that a lovely surprise? thanks. :guitar:

---

### Post by Open-SuSe-A-Me on 2009-01-12
Hey everyone, fwojciec's suggestion worked for me to fix the gtk theme.  
I decided that trying to get Arch to work properly on my laptop wasn't going to happen, so i did a distro swap between my desktop and laptop.  I threw Hardy on the laptop (works fine, as always) but now i have to deal with trying to get my Nvidia card working with Arch on my desktop as well as it did in Hardy (near-perfect) and its making me insane.  I did all the "nvidia-settings" modifications that i had on Hardy but i'm still getting wobbly window and 3D cube tearing (only sometimes, which is the weird part that I dont understand).

Generally i can live without Compiz but i payed good money for this card, and people's first time reactions (usually windows folks) are priceless!

---

