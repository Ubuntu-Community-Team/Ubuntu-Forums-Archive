---
title: "Why do apps start slowly from menu bar?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by KevlarGurra on 2006-09-19
Hi!

I have put som apps in the menu bar (the one at the top) like firefox, thunderbird and the terminal window. When I click them, they don't start immediately like they would when I start them from the Applications menu, instead there's a yellow frame or something zooming out from the icon in a very ugly way... Can I somehow make them start as quick as they should?
I have compiz installed by the way, I don't know if that could be interfering but I think I had this issue before I installed compiz as well.

---

### Post by Brunellus on 2006-09-19
those black lines are GNOME issue.  the default GNOME window manager draws them, too, and I am really at a loss to understand why the GNOME devs think it's a cool thing.

---

### Post by jordanmthomas on 2006-09-19
Press <Alt>+F2
type
```
gconf-editor /desktop/gnome/interface
```
Uncheck enable_animations
poof!  They are gone

---

### Post by KevlarGurra on 2006-09-20
Nope, I've turned it off, restarted (and checked that animations are still off) but they're still there...

---

