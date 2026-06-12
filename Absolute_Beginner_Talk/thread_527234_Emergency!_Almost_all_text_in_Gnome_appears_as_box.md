---
title: "Emergency! Almost all text in Gnome appears as boxes today's software update!"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by punong_bisyonaryo on 2007-08-16
Anybody! Please help!

I'm not sure if I got a virus, or just a bad update. First, I'm browsing posts in Liferea and Firefox, some Software Updates appear in update manager, 3 updates. libsomething related to codecs. And then all of a sudden, when I open evince, all boxes! Some programs crash, more boxes. I try restarting, even gdm login shows boxes! Now everything, my Applications, Places, System, clock, even the text in desktop icons appear as boxes!

How do I fix or rollback or whatever?

Extreme panic!:confused:

---

### Post by Sunflower1970 on 2007-08-16
Have you tried rebooting?

I've seen this happen to me before, but it was only when I was upgrading between Edgy and Feisty.

---

### Post by Soybean on 2007-08-16
Well, first of all, don't panic. I'm sure it can be fixed. :)

Second, it's unlikely that it's a virus or a bad update. Linux viruses are essentially unheard-of, and a bad update would likely be affecting a lot of people and resulting in a lot of related forum posts. That's not to say that it's definitely not either of those things... just that they're not super likely.

So... what else have you done recently that might have inadvertantly caused this? Perhaps something involving language settings... or fonts... or internationalization? Or maybe a new theme that you downloaded from the internet?

Oh, and Sunflower has a point -- rebooting is often worth a shot. ;)

---

### Post by punong_bisyonaryo on 2007-08-16
> **Sunflower1970 said:**
> Have you tried rebooting?

I've seen this happen to me before, but it was only when I was upgrading between Edgy and Feisty.

Thanks for taking time to look at my post. It's been a full 13 minutes!

Yes I have. A note, before I restarted, all the gnome apps that were already open had no problems, it's just the newly opened ones. Naturally, when I rebooted, GDM, gnome desktop, even the text inside gedit all appear as boxes.

I'd like to know which updates they were today for Edgy, and how to roll them back, if that will help.

Another note, I feel blind as I can't understand anything on my system (good thing it didn't affect firefox). Menus are unreadable, which includes everything inside synaptic, etc.

---

### Post by punong_bisyonaryo on 2007-08-16
> **Soybean said:**
> Well, first of all, don't panic. I'm sure it can be fixed. :)

Second, it's unlikely that it's a virus or a bad update. Linux viruses are essentially unheard-of, and a bad update would likely be affecting a lot of people and resulting in a lot of related forum posts. That's not to say that it's definitely not either of those things... just that they're not super likely.

So... what else have you done recently that might have inadvertantly caused this? Perhaps something involving language settings... or fonts... or internationalization? Or maybe a new theme that you downloaded from the internet?

Oh, and Sunflower has a point -- rebooting is often worth a shot. ;)

Nothing new installed except those updates before my pc got whacked. My virus-phobia is getting the best of me. I should know better that there are virtually no viruses in Linux, it's the reason I migrated from M$.

Absolutely nothing new. I have glib, pango, compiled from source (I want to learn gnome programming), but I've already rebooted after that and my computer worked fine. Then I turned my computer off again to go to work this morning.

Before I updated, I noticed that my hard disk light was on for some reason (I thought it was strange). Though I only had Liferea and firefox on.

---

### Post by irish_flu on 2007-08-16
It's not a virus.

It looks like there's a font problem.  Can you see well enough to get to the desktop font control panel?

It's located in the System menu (just to the left of your "terminal" shortcut there on the top panel), inside "Preferences".  

If you have trouble finding it with all the boxes: for me , "Preferences" is the first choice under "System", and "Font" is the seventh one down in the Preferences menu.

Try setting the Desktop and Application fonts to "sans" or something.

If that doesn't work (or if it's so messed up that you can't tell what you're doing), open up terminal and type
```

sudo apt-get install xfonts-base

sudo apt-get install xfonts-scalable

sudo apt-get install xfonts-75dpi

```

and then reboot (or restart Gnome with CTRL+ALT+SHIFT+Backspace).  This should help if your fonts  are somehow missing.

---

### Post by punong_bisyonaryo on 2007-08-16
> **irish_flu said:**
> It's not a virus.

It looks like there's a font problem.  Can you see well enough to get to the desktop font control panel?

It's located in the System menu (just to the left of your "terminal" shortcut there on the top panel), inside "Preferences".  

If you have trouble finding it with all the boxes: for me , "Preferences" is the first choice under "System", and "Font" is the seventh one down in the Preferences menu.

Try setting the Desktop and Application fonts to "sans" or something.

If that doesn't work (or if it's so messed up that you can't tell what you're doing), open up terminal and type
```

sudo apt-get install xfonts-base

sudo apt-get install xfonts-scalable

sudo apt-get install xfonts-75dpi

```

and then reboot (or restart Gnome with CTRL+ALT+SHIFT+Backspace).  This should help if your fonts  are somehow missing.

Well, I did manage to get to the Font (it's the 4th one on my system, I could tell with the icon). But upon opening, even the font names were boxes.

I tried aptitude installing, but I already had them.

I think my messing around with pango caused the problem. When I run gedit from terminal, I get a few warnings like:

```
sys:1: PangoWarning: pango_shape called with bad font, expect ugly output
sys:1: PangoWarning: pango_font_get_glyph_extents called with null font argument, expect ugly output
sys:1: PangoWarning: pango_font_get_metrics called with null font argument, expect ugly output
sys:1: PangoWarning: pango_font_get_font_map called with null font argument, expect ugly output
sys:1: PangoWarning: _pango_cairo_font_map_get_renderer: assertion `PANGO_IS_CAIRO_FONT_MAP (fontmap)' failed
sys:1: PangoWarning: _pango_cairo_font_install called with bad font, expect ugly output
```

Funny thing is, even with this pango mess I was able to boot into my system with no problem. It only got weird after the software update. Could it be my mess caused the software update to mess up, making even more mess?

---

### Post by Bachstelze on 2007-08-16
To check if it's only a Gnome problem ore a more broad one, try to stop your X (sudo /etc/init.d/gdm stop) and run *startx* in a virtual console. It should start fvwm. Yes, I know it's ugly, but do fonts appear correctly ?

---

### Post by punong_bisyonaryo on 2007-08-16
Note, I'm not very good at installing from source, except those that work after ./configure and sudo make install. Trying to install GTK is a nightmare! Too many dependencies. I managed to install glib and pango, but not cairo. has some libpng dependencies, and I couldn't understand installing libpng. I wanna get rid of 'em, but is there a make uninstall or unmake or something?

---

### Post by punong_bisyonaryo on 2007-08-16
> **HymnToLife said:**
> To check if it's only a Gnome problem ore a more broad one, try to stop your X (sudo /etc/init.d/gdm stop) and run *startx* in a virtual console. It should start fvwm. Yes, I know it's ugly, but do fonts appear correctly ?

What's fvwm? I tried doing startx but it only booted my gnome again.

---

### Post by Bachstelze on 2007-08-16
Cloxe X (Ctrl+Alt+BkSpace),

```
mv .xinitrc .xinitrc.old
```

then startx again.

---

### Post by punong_bisyonaryo on 2007-08-16
> **HymnToLife said:**
> Cloxe X (Ctrl+Alt+BkSpace),

```
mv .xinitrc .xinitrc.old
```

then startx again.

managed to restart X, now I know why you say it's ugly. No change.

---

### Post by Bachstelze on 2007-08-16
Open a terminal and run a *sudo apt-get update && sudo apt-get dist-upgrade*, any errors ? I didn't get that problem here.

---

### Post by punong_bisyonaryo on 2007-08-16
> **HymnToLife said:**
> Open a terminal and run a *sudo apt-get update && sudo apt-get dist-upgrade*, any errors ? I didn't get that problem here.

Err, wait, I'm not gonna do a dist-upgrade. Not yet anyway, coz my wireless don't work in Feisty.

I think I've broken my system for good. In my panic and haste, I tried searching for a way of uninstalling source packages, so I did a *make -n uninstall* to pango, glib, pkg-config and libpng. I restarted with no change. But when I tried to remove libpango1.0-0 (I was going to remove then reinstall it), it listed A LOT of broken dependencies, and it timed out looking for a solution, so I told it to look harder, 3x, still no solution with 20,000+ open, 14000+ closed, and 700+ conflict/broken.

Maybe a reinstall is easier since my home is on a separate partition anyway...

---

### Post by punong_bisyonaryo on 2007-08-16
> The &#64257;rst thing to do, of course, is download the GTK source and install it. You can
always get the latest version from ftp.gtk.org

They make it sound so easy. The GTK tutorial should have a warning: Before you get into GTK programming, you need to be quite adept at installing things from source first. I think I'll steer clear of trying to learn GTK for now, unless there's an easier way of installing it.

Anyway, I've decided on just wiping my system and reinstalling, it'll take me a good 20mins or so, but it's ok. Since my /home is on another partition, wouldn't be too painful (not as painful as the damage I've caused).

To everyone, you've all been very kind and helpful. Even if I wasn't able to solve this, or rather, since my problem was beyond a state of repair, thank you all!

---

### Post by irish_flu on 2007-08-17
> **punong_bisyonaryo said:**
> They make it sound so easy. The GTK tutorial should have a warning: Before you get into GTK programming, you need to be quite adept at installing things from source first. I think I'll steer clear of trying to learn GTK for now, unless there's an easier way of installing it.

Anyway, I've decided on just wiping my system and reinstalling, it'll take me a good 20mins or so, but it's ok. Since my /home is on another partition, wouldn't be too painful (not as painful as the damage I've caused).

To everyone, you've all been very kind and helpful. Even if I wasn't able to solve this, or rather, since my problem was beyond a state of repair, thank you all!

I'd probably end up doing the same thing, man.  Unless you enjoy spending hours troubleshooting something (and sometimes I do enjoy it, hehe) it's often simpler to blow away the OS and start fresh.  IMHO that applies to Linux, Windows, and OSX pretty equally.

---

### Post by punong_bisyonaryo on 2007-08-18
> **irish_flu said:**
> I'd probably end up doing the same thing, man.  Unless you enjoy spending hours troubleshooting something (and sometimes I do enjoy it, hehe) it's often simpler to blow away the OS and start fresh.  IMHO that applies to Linux, Windows, and OSX pretty equally.

Good thing about Linux when you decide to take this route, if you made necessary preparations, reinstalling is a breeze. Having a separate home partition and scripts to add repositories and install programs, it's almost automatic. You can have your old system back before a Windows reinstall finishes.

---

### Post by nvteighen on 2007-08-18
Just something... I suspect there's a big issue with GTK and fonts. I had to do a reinstall because GNOME fonts began to show unreadable (not as boxes) after I had checked KDE out. I had lots of research and the only thing I could conclude is that something (maybe Qt) may have corrupted GTK.

Could it be time for the GNOME-people to check GTK's code?

---

### Post by DarinB on 2007-08-23
I just had the same problem. i had added windows fonts from a thumb drive via a new directory in my /usr/share/fonts/truetype/ directory i added a myfonts directory and put them there.  I ended up with boxes and blind just like you
what i did was sleep on it and got up with the idea to either change the ownership of the folder or rm   it i just rm it via terminal i used sudo su
password >> went in to the directory where the .ttf and .TTF's are and rebooted it worked and i am back to normal.

good luck

db

---

