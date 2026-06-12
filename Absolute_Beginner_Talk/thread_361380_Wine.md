---
title: "Wine"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-02-14
How do I use WINE? I think I installed it from the Add/Remove programs feature on Ubuntu GNOME...

I basically want to install Photoshop.

---

### Post by taurus on 2007-02-14
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

[http://www.winehq.com/site/documentation](http://www.winehq.com/site/documentation)

---

### Post by energiya on 2007-02-14
just
```

cd /path/of/your/file.exe
wine file.exe

```

and don't forget to do a
```

winecfg

```
to configure it as you need.

---

### Post by Shay Stephens on 2007-02-14
Firstly, what version of Photoshop are you trying to install?  If it is one of the CS versions forget it.  If it is version 7 or lower, good, that can work.

**Check your version of wine**
You will need wine version .9.52, .9.52 has made running Photoshop 7 a snap and the little glitches with the pallets are gone.  You can check your version by running this in the terminal:
```
wine --version
```

If you need an older (or newer) version of wine, you can get them from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

If you want to uninstall the currently installed version of wine, use synaptic to remove it.  Then double click the wine deb you downloaded to install that version.  Once your version of wine is installed, run the configuration from the terminal:
```
winecfg
```
You don't have to change any settings.  You can accept the defaults and close it after it pops up.

**Installing Photoshop**
In order to install Photoshop 7 or lower, load the CD and right click on the setup.exe program and run with wine.  Or use the terminal:
```
wine /media/cdrom0/Photoshop/Setup.exe
```

**Create a launcher**
If a launcher is not made and you have to make one yourself, right click where you want the launcher, select "create launcher"
   [LIST=1]
[*]Type in a descriptive name (e.g.Photoshop)
[*]   Type in the command (e.g. wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe")
[*]   Add a comment if desired (e.g. Edit photos)
[*]   Click on the button that edits the icon. choose a generic icon or navigate to one you have saved already.
[/LIST]

Using the windows path to run the program works best rather than using the linux path to the program.  Using the linux path in the past has killed the ability to "Save for web" in Photoshop.  So stick with the windows path for now.

And that's it, you should be able to run Photoshop 7 or lower.

---

### Post by Baelfael on 2007-02-15
Damn, well forget that. I was hoping to install CS2. 7 is okay, I have it, but the brush support turns me off, and I depend a lot on brushes when graphic designing. Oh well, I'll just use my fathers computer for Photoshop, and maybe I'll learn the GIMP. Thanks everyone.

---

### Post by nphx on 2007-04-23
> **Shay Stephens said:**
>  The pallet will not minimize when you minimize Photoshop, and it won't stay in a single workspace, the pallet will span all workspaces.  So close Photoshop when you are done with.

A quick fix for this is before minimizing Photoshop hit the TAB key on your keyboard, this will hide all the pallets in Photoshop. To get the pallets back you hit TAB again.

---

### Post by kc5hwb on 2007-04-23
Why won't Photoshop CS or CS2 work in WINE?  Do they work in VMware?

---

### Post by Shay Stephens on 2007-04-23
> **nphx said:**
> A quick fix for this is before minimizing Photoshop hit the TAB key on your keyboard, this will hide all the pallets in Photoshop. To get the pallets back you hit TAB again.

Brilliant!!!  Thank you!

---

