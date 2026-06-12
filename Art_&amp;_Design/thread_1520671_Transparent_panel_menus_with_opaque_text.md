---
title: "Transparent panel menus with opaque text"
date: 2010-06-29
forum: Art &amp; Design
---

### Post by goseph on 2010-06-29
Hi,

I know that with compiz you can make the panels semi-transparent but this makes the text transparent and unreadable, has anybody come across a good way to have transparent panels with opaque text a la my mockup?

---

### Post by TheWeakSleep on 2010-06-30
How about setting it to a transparent solid color via properties? or using a transparent background image?
It's not really true transparency, though that's all I can think of at the moment :)

---

### Post by ankit.vader on 2010-06-30
System->preferances->compiz settings manager->Opacity and Saturation

then under  Window Specific Settings add this

"Menu | PopupMenu | DropdownMenu"

 and set it whatever transparency you want.

---

### Post by TheWeakSleep on 2010-06-30
In the original post they said that they didn't want to use compiz because it made the text transparent as well. Maybe you could use a combination of a transparent background and compiz to get the effect you want? 
The thing with having a transparent solid color or a transparent background image is that it isn't true transparency. That means that if you have a panel on the bottom, you wouldnt be able to see a window if you dragged it underneath, but you could see the background.

On a top panel, it wasn't so much as an issue for me, but maybe if you play with compiz you'll be able to get the effect good enough :)

I don't believe the gnome-panel has support for transparency, but i could be completely wrong :) if anyone else knows more, I'd be interested to hear this as well :)

---

### Post by goseph on 2010-06-30
Thanks for the replies chaps!

Unfortunately. a transparent background image doesn't actually render as transparent, when set as the menu background, the panel can be set as transparent but not the menu and as was mentioned earlier, compiz makes the text transparent rendering the meus unusable. I found a tool called GNOME color chooser but that doesn't support transparency either. I fear that I may be asking the impossible, people like me just need to quit bitching and switch to KDE :p

---

### Post by TheWeakSleep on 2010-06-30
Have you tried using the blur windows plugin for compiz? maybe that would make it easier to read them. Other then that, all I can think of is replacements for the gnome-panel like awn or docky, they have some menu applets for them and are pretty customizable.

Sorry I couldn't help any more than that

---

### Post by vexxev on 2010-11-21
This doesn't really solve the issue... well it does, but it isn't a gnome solution.  You could run kwin instead of compiz and you would have the ability to make transparent menus (on the panel, and applications) while keeping the text opaque

---

