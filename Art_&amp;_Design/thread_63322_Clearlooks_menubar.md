---
title: "Clearlooks menubar"
date: 2005-09-07
forum: Art &amp; Design
---

### Post by wtd on 2005-09-07
I'm using Clearlooks with the Blended Metacity theme, and I love the effect, but I'm wonder if there's any way to remove the visible border at the bottom of the menubar, to accomplish an even more smooth look?

---

### Post by bvc on 2005-09-08
You are supposed to be able to control that in the gtkrc;
```
engine "clearlooks"
   {
    menubarstyle      	= 0       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     	= 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle 		= 1       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  	= 0       # 0 = candy bar, 1 = flat
  }
}
```
but I have never seen a diff between;
menubarstyle= 0
and
menubarstyle= 1

I'm not a clearlooks-devel but I would guess 'flat' should do it...but it does not.

---

### Post by fredbird67 on 2008-02-01
I just tried changing the menuitemstyle in the "Ubuntu-Red" theme I downloaded from gnome-look.org from 1 to 2, and I swear I can't tell a difference there, either.  What's up with that?

---

