---
title: "Does this work on Ubuntu?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-13
I thinking about buying a new mouse, as Ubuntu dont work very well with my M$ Mouse.

I am thinking about buying this one:
[http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2142,CONTENTID=11551](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2142,CONTENTID=11551)

But I it says it support M$ and MAC? 
Will I be able to use this on Ubuntu?

---

### Post by zerhacke on 2006-04-13
Hardware companies have a thing about saying it works with Linux if they already said it works with MS.

It should work, it's a basic USB mouse.  It's almost identical to mine, and mine works fine.  Should autodetect and setup right out of the box.

---

### Post by jimrz on 2006-04-13
Check [[COLOR="Sienna"]_**this**_[/COLOR]]("http://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons?highlight=%28intellimouse%29") might fix your current mouse or help you get everything working on a new one. I have both M$ and Logitec mice functioning correctly on breezy machines.

---

### Post by BarFly on 2006-04-13
I'm using a Logitech G5 without any problems.  I think they do not say it will work for Linux because they don't have a driver for it.  Forget about using the side scroll feature and the back button does the same thing as clicking the scroll wheel instead of going back a page.  Other than that, it will work.

---

### Post by cdgore on 2006-04-27
[QUOTE=BarFly]I'm using a Logitech G5 without any problems.  I think they do not say it will work for Linux because they don't have a driver for it.  Forget about using the side scroll feature and the back button does the same thing as clicking the scroll wheel instead of going back a page.  Other than that, it will work.[/QUOTE]

You can get all the G5's buttons to work by putting this in your xorg.conf:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Protocol" "evdev"
Option "Dev Name" "Logitech USB Gaming Mouse"
Option "Buttons" "12"
Option "ZAxisMapping" "4 5 7 6"
Option "Resolution" "2000"
EndSection

---

