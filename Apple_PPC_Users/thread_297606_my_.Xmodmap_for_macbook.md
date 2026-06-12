---
title: "my .Xmodmap for macbook"
date: 2006-11-11
forum: Apple PPC Users
---

### Post by est on 2006-11-11
Hello all,

I created an xmodmap file to make the keys on a British macbook do what they say they should. Don't know if this would be equally useful for ibook, macbook pro, powerbook or what.

Looks like this: 
```

! Get \, |, @, ", ~, ` as advertised.
keycode 51 = backslash bar
keycode 11 = 2 at EuroSign
keycode 48 = apostrophe quotedbl
keycode 12 = 3 sterling numbersign
keycode 13 = 4 dollar cent
keycode 49 = grave asciitilde

! Apple_L as mode switch (to get #, €, etc.)
keycode 115 = Mode_switch

! Additional ctrl at capslock.
!remove Lock = Caps_Lock
keycode 66 = Control_L
add Control = Control_L

! random key left of 1 as compose/ Meta_L/ Super_L
keycode 94 = Multi_key Meta_L Super_L

! numlock (numlock is working, but the numbers aren't...)

```

It gives you an extra control instead of capslock, and a Multi_key/  Compose at the weird key left of 1.

Apple+3 gives you #, Apple+2 gives you the eurosign, etc.

I haven't been able to get numlock to work properly, when numlock is on and you press `j', no key seems to be generated. :(

It's fairly well commented so you should be able to comment out the bits you don't need. Just save it as ~/.Xmodmap and run xmodmap ~/.Xmodmap. 

GNOME should pick it up automatically so you could just restart GNOME instead.
-edd

---

