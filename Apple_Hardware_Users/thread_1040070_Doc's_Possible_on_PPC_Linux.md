---
title: "Doc's Possible on PPC Linux?"
date: 2009-01-15
forum: Apple Hardware Users
---

### Post by McFrostey on 2009-01-15
I use to use OSX then when I switched to Linux I was told that I can still use "Doc's" and theres a variety of them, so are they possible with the PPC?
When I go to System>Administration>Hard Drivers

my graphics card does not show up, since I'm using  a Nvidia, its an old one since im using a powerPC G4 from and iMac...:confused:

---

### Post by phoenixphyre on 2009-01-15
> **McFrostey said:**
> I use to use OSX then when I switched to Linux I was told that I can still use "Doc's" and theres a variety of them, so are they possible with the PPC?
When I go to System>Administration>Hard Drivers

my graphics card does not show up, since I'm using  a Nvidia, its an old one since im using a powerPC G4 from and iMac...:confused:

im wondering if the Nividia card you have is a "restricted" card. Mine was and i got the plug ins to be able to use it.

go to SYSTEM> PREFERENCES> APPEARANCE
then click on the "visual effects" tab, choose the "extra" and tell us what happens.

---

### Post by stream303 on 2009-01-15
The special affects like compiz,etc are not available for most Macs, especially those using the opensource 2D nv driver like ours.

Nvidia does not provide a proprietary binary video driver for ppc.  For me, that's a good thing. :)

Ok, so 3D and special affects are out.  However, if you are looking for a little more oomph to your video, consider if you **really** need a 24-bit color depth and drop it back to 16 bits.

Since we are limited to the 2D driver, why not make it as efficient as possible?  If you don't do any *critical* graphics / photo editing, 16 bits may be just fine for general purpose browsing, word processing, even general purpose photo viewing.

In fact, I do this on all the machines I have unless I am actuall editing photos in Gimp, etc.

Here's a snippet from my /etc/X11/xorg.conf file where I force the use of 16 bits, rather than the default of 24 by adding two lines to force it:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        **DefaultDepth    16**
                SubSection "Display"
                **Depth 16**
                EndSubSection
EndSection

```

Your "Section Screen" may look a bit different, or possibly need to be added manually to make this happen, but the DefaultDepth and Depth lines help make this happen.

About the only thing you'll see right off the bat is that gradients won't be exactly smooth.  However, you should see an immediate boost in speed.

Something worth trying anyway.

---

### Post by inigomontoya on 2009-01-18
Just a shot in the dark here, but would Metacity's built in compositing work with the nv driver?  You don't necessarily have to use compiz.

---

