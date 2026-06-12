---
title: "Keyboard mapping"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by Dark_Lotus on 2008-03-24
Does anyone have a table for KeyCodes? I want to map the Apple key to the ctrl key and the ctrl key to right click, if that makes since. So I want to be able to press Apple + T for a new tab and Apple + W to close the window and be able to hold down the CTRL key and click for right click. Or is there a way to enable one finger on the right corner and click as right click?

---

### Post by afterkelsen on 2008-03-24
Have a look at the touchpad ideas here:
[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

If you need to figure out what keycodes the different keys generate then simply run the utility "xev" from a terminal. When the program launches you see a window, as long as the window has focus all the keypresses and mouse movements will be shown in the terminal from which you launched xev.

---

### Post by xeth_delta on 2008-03-24
> **Dark_Lotus said:**
> Does anyone have a table for KeyCodes? I want to map the Apple key to the ctrl key and the ctrl key to right click, if that makes since. So I want to be able to press Apple + T for a new tab and Apple + W to close the window and be able to hold down the CTRL key and click for right click. Or is there a way to enable one finger on the right corner and click as right click?

Have a look at the link afterkelsen suggested. I have remapped several of the keys on my Macbook using xmodmap.

About the trackpad, does tapping with three fingers not provide a right click? It does on my computer.

---

### Post by eitan on 2008-03-24
this is my ~/.xmodmap in which i just swap control and super on a macbook pro:

!
! Swap Control_L and Super_L
!
remove mod4 = Super_L
remove control = Control_L
keysym Control_L = Super_L
keysym Super_L = Control_L
add mod4 = Super_L
add control = Control_L

that does half of what you've asked for.

/ eitan

---

### Post by Dark_Lotus on 2008-03-24
What is the Super key?

---

### Post by xeth_delta on 2008-03-24
If I am not mistaken, the super key, would be, in the case of a Mac keyboard, the Mac key.

---

### Post by cyberdork33 on 2008-03-24
> **xeth_delta said:**
> If I am not mistaken, the super key, would be, in the case of a Mac keyboard, the Mac key.
yes, or the windows key on a typical PC keyboard.

---

