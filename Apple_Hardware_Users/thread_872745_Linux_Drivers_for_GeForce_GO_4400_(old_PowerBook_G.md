---
title: "Linux Drivers for GeForce GO 4400 (old PowerBook G4)"
date: 2008-07-28
forum: Apple Hardware Users
---

### Post by nogoodreason on 2008-07-28
Hi guys.

I've just installed Hardy Heron (Power PC edition) on my dad's old PowerBook G4.  I formatted the drive, so Ubuntu is the only OS.

While it seems to be running well, the graphics are a bit funny in places (particularly at bootup), but I can't find any drivers for the graphics card.  According to Wikipedia, it's probably an Nvidia GeForce GO 4400.  There are no 32-bit Linux drivers for it on the Nvidia website.

Does anyone know where I could find some drivers for this card?

---

### Post by stream303 on 2008-07-28
The good news is that to keep it simple, there are no available nvidia drivers for ppc other than what you have now. :)

Other than the splash screen, what other problems are you having with video?

One nvidia option you can apply beyond the standard install is to use dithering, that is by adding this line to your /etc/X11/xorg.conf file manually:

```
Section "Device"
        Identifier      "Configured Video Device"
        **Option          "FPDither" "true"**
EndSection
```

Which should prove helpful on anyone using the nv driver with an lcd screen.  Try it and see.

As for the splash screen, it has never looked good on ppc for most (there are exceptions), and one thing you can do is opt to see the dmesg at boot time instead.  You do this by specifying "nosplash" in your /etc/yaboot.conf file with the append= line.

When modifying your yaboot.conf file, be sure to make the system aware of it with
sudo ybin -v -C /etc/yaboot.conf

---

### Post by Steveway on 2008-07-28
If that is not a productivity-system then you could also upgrade to Intrepid Ibex and use the nouveau driver. It gives you basic 3D-capability and pretty good 2D-capability (Varies between models.). I'm using it right now with a Go5200 on a normal x86 PC and it works pretty well.

---

### Post by nogoodreason on 2008-07-28
And here I show my ultimate n00bishness when it comes to Linux:

I'm trying to edit the xorg.conf file using 'gedit', but it won't let me save the altered document (as I do not have the necessary permissions).

How do I grant 'sudo' privileges to myself within 'gedit'?  (Do I need to open it up via the Terminal, perhaps?  And if so, how?)


Thanks for your responses.  I will try them as soon as it lets me save my changes. :)

---

### Post by Steveway on 2008-07-28
Use:
```
gksu gedit /etc/X11/xorg.conf
```
But be carefull, and don't change anything where you don't know how to revert it back later.

---

### Post by cyberdork33 on 2008-07-28
> **Steveway said:**
> But be carefull, and don't change anything where you don't know how to revert it back later.
That is why you should backup your config files before editting...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

