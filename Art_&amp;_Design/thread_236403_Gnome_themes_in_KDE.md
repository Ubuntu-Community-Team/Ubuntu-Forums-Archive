---
title: "Gnome themes in KDE?"
date: 2006-08-14
forum: Art &amp; Design
---

### Post by janhenderson on 2006-08-14
When I was using Gnome as my desktop environment I used kcontrol started from the command line to theme kde to fit in with gnome. Now that I'm using kde the gnome applications use a rudinementary theme that I don't like and doesn't fit in (it's not human controls, and not nuovext icons), how do I theme the gnome apps within KDE to use human controls and nuovext icons when KDE is my desktop environment? Thanks.

---

### Post by janhenderson on 2006-08-14
> **janhenderson said:**
> When I was using Gnome as my desktop environment I used kcontrol started from the command line to theme kde to fit in with gnome. Now that I'm using kde the gnome applications use a rudinementary theme that I don't like and doesn't fit in (it's not human controls, and not nuovext icons), how do I theme the gnome apps within KDE to use human controls and nuovext icons when KDE is my desktop environment? Thanks.

I found the answer; "gnomecc &" while in KDE

There are two ways to install GTK themes.

If you use GNOME, you can manage themes with the GNOME control center. Launch it with "gnomecc &", then navigate the menus to "Desktop --> Theme selector". Click on "Install new theme..." and point it toward the tarball. There's no need to unpack it.

If you don't use GNOME (or don't want to bother with gnomecc), you can use Gtk Theme Switch, which can switch themes from the commandline or sit on the GNOME Panel for quick access.

---

### Post by janhenderson on 2006-08-14
> **janhenderson said:**
> I found the answer; "gnomecc &" while in KDE

There are two ways to install GTK themes.

If you use GNOME, you can manage themes with the GNOME control center. Launch it with "gnomecc &", then navigate the menus to "Desktop --> Theme selector". Click on "Install new theme..." and point it toward the tarball. There's no need to unpack it.

If you don't use GNOME (or don't want to bother with gnomecc), you can use Gtk Theme Switch, which can switch themes from the commandline or sit on the GNOME Panel for quick access.

Oh nevermind. That didn't stick. I found it again. It's under kcontrol/Appearance/GTK styles and fonts/ and then tell it to use another style which is human instead of using kde styles in GTK applications. You could also tell it to use another font if you want.

---

### Post by ComplexNumber on 2006-08-14
> and point it toward the tarball. There's no need to unpack it.
thats not a good idea ;). its best not to use the theme manager to install themes because many theme tarballs contain more than 1 theme, so installation of the tarball via theme manager will fail. try it out for yourself on something like [this]("http://www.gnome-look.org/content/show.php?content=43696") which contains more than 1 theme.
its best to unpack themes and place them directly in /home/<username>/.themes

---

### Post by gruvsyco on 2006-08-15
I'd like to find out where KDE stores it's theme info for GTK apps so I can create symlinks to my actual Gnome setup.

If I set the GTK stuff in KDE's control center, it screws up everything in Gnome, if I unset it, Gnome works fine again but GTK apps in KDE look like crap.

Anyone have any ideas?

---

### Post by janhenderson on 2006-08-15
> **gruvsyco said:**
> I'd like to find out where KDE stores it's theme info for GTK apps so I can create symlinks to my actual Gnome setup.

If I set the GTK stuff in KDE's control center, it screws up everything in Gnome, if I unset it, Gnome works fine again but GTK apps in KDE look like crap.

Anyone have any ideas?

Just tell KDE not to theme GTK stuff. I mentioned above how to do that.

---

### Post by gruvsyco on 2006-08-15
I don't know if there is something bizaar with my KDE install but if I do that then GTK based apps in KDE look like crap.

---

### Post by janhenderson on 2006-08-15
> **gruvsyco said:**
> I don't know if there is something bizaar with my KDE install but if I do that then GTK based apps in KDE look like crap.

Well tell KDE not to theme GTK apps, then change the GTK theme with "gnomecc &" at the command line, to bring up the gnomecc gui, to one you like. I use human for GTK and plastik for KDE. It looks good.

---

