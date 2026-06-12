---
title: "2D animation and Wacom"
date: 2009-03-28
forum: Art &amp; Design
---

### Post by NerdcoreSteve on 2009-03-28
I am using a cool 2D animation program called [Pencil]("http://www.pencil-animation.org/") with my Wacom tablet. The pencil tool is pressure sensitive but the eraser tool is not. I've not got much luck with their forums so I thought I might ask here. Is there anything wrong with this xorg file? It works just fine with GIMP.

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "stylus"
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "eraser"
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "cursor"
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
EndSection

---

### Post by Favux on 2009-03-28
Hi NerdcoreSteve,

You didn't say what kind of tablet you have.  If you do not have an external Wacom mouse for it I don't think you need the "cursor" section or its entry in "ServerLayout".  And if the tablet has "pad" then you need to put it in "ServerLayout".  I think its:
```
        InputDevice     "pad"
```
In Gimp my eraser gives me a "pressure" effect depending on how hard I press it.  Is that what you're talking about?

I hope this is helpful.

---

### Post by NerdcoreSteve on 2009-03-28
Yes That's the kind of pressure I'm talking about and I am using an intuous.

---

### Post by Favux on 2009-03-28
Hi NerdcoreSteve,

What's your stylus pressure sensitivity curve look like in /home/username/.xinitrc?  The .xinitrc (hidden file) should have been generated after running wacomcpl.  Since the stylus and eraser have the same input path and coordinates I assume the pressure curve for stylus is what I see with eraser in Gimp.  Do you see "pressure" in Gimp?  Maybe Pencil just doesn't offer that?

---

### Post by Favux on 2009-04-04
Hi NerdcoreSteve,

I went ahead and installed Pencil.  I can get pressure with my stylus, more obvious with the paint brush.  It sort of works for the eraser.  But rather than the feathering I think you want what I see is light pressure equals a narrow "line" erased and the harder I press the wider it gets up to where eraser is set.

It didn't behave like this when I started it.  I just fooled around (no tutorial read) and I think it was going to Edit>Preferences>General where I enabled one of the gradients.

Since I was fooling around, don't take this as gospel.  The point is that it does recognize pressure.

---

