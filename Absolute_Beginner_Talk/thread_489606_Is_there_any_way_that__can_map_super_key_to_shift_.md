---
title: "Is there any way that  can map super key to shift key?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by margaritaville on 2007-07-01
My shifts dont work at all for some reason. (ate by coffee)
And I tried using .xmodmaprc with
keysym Super_L = Shift_L

It works under console fortunately, but doesn't on gnome programs at all, like gedit.

I am just wondering if there is any way that I can use to map super key to shift on gnome.

Thank you

---

### Post by greg_g on 2007-07-01
I don't know personally, but try searching ("googling") for "x keymap" add in "howto" "guide" or whatever.

I found some stuff that way, but it got really technical pretty quick, so good luck.

greg

---

### Post by Bluecircle on 2007-07-01
I'm pretty sure when you configure X you can do custom keymaps.

run

```

sudo dpkg-reconfigure xserver-xorg

```

When you get to the keyboard settings there should be a part where you can set the windows key to work as a shift.

---

