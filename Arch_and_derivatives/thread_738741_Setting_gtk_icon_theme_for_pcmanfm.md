---
title: "Setting gtk icon theme for pcmanfm"
date: 2008-03-28
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-03-28
I've installed Arch on my old PC with fluxbox and I'm having a problem with the file manager I'm trying to use, pcmanfm.  It isn't displaying any icons at all.  I've extracted the theme UltimateGnome from gnome-look into ~/.icons.  I then created a file in my home directory called .gtkrc-2.0 and added the line gnome-icon-theme-name="UltimateGnome".  These were instructions that were given when I first installed pcmanfm.  I rebooted the computer after doing that, but there are still no icons showing up.  Did I do something wrong?  I use Ubuntu on my primary computer so I don't have to worry about these things.

Also, I dunno if this may have something to do with it, but when I launch pcmanfm from the terminal, I get this error message.  Could this have something to do with not loading my icons?

```

[nelson@beta-pc ~]$ pcmanfm

(pcmanfm:4970): Gtk-WARNING **: Could not find the icon 'gnome-fs-directory'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
        http://icon-theme.freedesktop.org/releases

(pcmanfm:4970): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by K.Mandla on 2008-03-29
Some of those icon themes are distributed as svn files. ... Last time I tried, they had to be png files (or maybe jpg is okay, I forget), so that might be an issue.

---

### Post by RedSquirrel on 2008-03-29
> **TheOrangePeanut said:**
> I've installed Arch on my old PC with fluxbox and I'm having a problem with the file manager I'm trying to use, pcmanfm.  It isn't displaying any icons at all.  I've extracted the theme UltimateGnome from gnome-look into ~/.icons.  I then created a file in my home directory called .gtkrc-2.0 and added the line gnome-icon-theme-name="UltimateGnome".  These were instructions that were given when I first installed pcmanfm.  I rebooted the computer after doing that, but there are still no icons showing up.  Did I do something wrong?

Try:

```
gtk-icon-theme-name = "UltimateGnome"
```Also, make sure that the theme name you use matches exactly the icons directory name under ~/.icons.

No need to reboot, by the way. When you change these GTk+ settings, they will apply to any applications you open after making the change.

---

### Post by TheOrangePeanut on 2008-03-29
Whoops, I actually put gtk-icon-theme-name, not gnome-theme-icon-name.  The directory matches the name I used in the gtkrc-2.0 file.  The files are .svn, though, so maybe that ended up being the problem.

I sort of fixed it; not how I'd like to, but now I have icons.  I ended up installing gnome theme's through pacman, and apparently pacman knew where to put them and how to configure them and I did not.  I installed the themes and ran pcmanfm and it worked off the bat.  Since I don't know how to add new themes I guess I'm stuck with what pacman installed, but it is way better than have no icons and no gtk themes at all :)

Thanks for trying to help guys.

---

### Post by Tenken on 2008-03-29
I use openbox/thunar, but this might work for you as well. Create a file name .gtkrc.mine in your home directory and add this line to it

```
gtk-icon-theme-name = "UltimateGnome"
```

---

### Post by K.Mandla on 2008-03-29
> **TheOrangePeanut said:**
> Whoops, I actually put gtk-icon-theme-name, not gnome-theme-icon-name.  The directory matches the name I used in the gtkrc-2.0 file.  The files are .svn, though, so maybe that ended up being the problem.
There are themes available in png, but I run into that problem every now and again where there's nothing to show for the theme I wanted. :(
> I sort of fixed it; not how I'd like to, but now I have icons.  I ended up installing gnome theme's through pacman, and apparently pacman knew where to put them and how to configure them and I did not.  I installed the themes and ran pcmanfm and it worked off the bat.  Since I don't know how to add new themes I guess I'm stuck with what pacman installed, but it is way better than have no icons and no gtk themes at all :)
Check the package search pages in Arch and in AUR; there are quite a few available under the search term "icon-theme."

[http://www.archlinux.org/packages/search/?repo=all&category=all&q=&limit=50](http://www.archlinux.org/packages/search/?repo=all&category=all&q=&limit=50)
[http://aur.archlinux.org/packages.php](http://aur.archlinux.org/packages.php)

As a matter of habit, I install gnome-icon-theme, hicolor-icon-theme and tango-icon-theme-extras, on every machine. After that, it's whatever I feel like. :D

---

### Post by RedSquirrel on 2008-03-31
> **TheOrangePeanut said:**
> Whoops, I actually put gtk-icon-theme-name, not gnome-theme-icon-name.  The directory matches the name I used in the gtkrc-2.0 file.  The files are .svn, though, so maybe that ended up being the problem.

I sort of fixed it; not how I'd like to, but now I have icons.  I ended up installing gnome theme's through pacman, and apparently pacman knew where to put them and how to configure them and I did not.  I installed the themes and ran pcmanfm and it worked off the bat.  Since I don't know how to add new themes I guess I'm stuck with what pacman installed, but it is way better than have no icons and no gtk themes at all :)

The method you described above is correct. You just extract the theme to ~/.icons and make the change to the line in ~/.gtkrc-2.0.

It was probably that particular theme that had some issues. You might try a few different themes and see if you can get it to work.

I have tried several themes but I most often just use Tango.

For GTK+ themes, you just extract them to ~/.themes.

For my GTK+ themes, I generally use Clearlooks as a base. I change some of its colours and turn off the colour on the scrollbar.

```
cp -r /usr/share/themes/Clearlooks ~/.themes/Clearlooks-custom
```Then in ~/.gtkrc-2.0:
```
gtk-theme-name = "Clearlooks-custom"
```


Edit: When you install icon themes from the repositories, they are in /usr/share/icons.

---

