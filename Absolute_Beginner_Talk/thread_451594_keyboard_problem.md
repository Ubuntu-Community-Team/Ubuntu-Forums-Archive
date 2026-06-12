---
title: "keyboard problem"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Quizzle on 2007-05-22
Help...

Problem:

 When I try to login to my ubuntu box the keys are wrong. My login name is "dillon" but i have to type something like sdeebe  to get it to come out right.  Once i'm logged in, though the keyboard is correct, it's only when I go to login. I'm pretty sure I know what caused it (me).  When I first installed I think I selected the wrong keyboard to use.. dunno how or why I did, but I'm pretty sure thats the cause.


Thanks

---

### Post by codesplice on 2007-05-22
Hi **Quizzle**,
Try going to System -->  Preferences --> Keyboard.  Click on the "Keyboard Layout" tab and make sure that "U.S. English" (or your layout of choice) is listed, and check the "Make Default" box to make sure.  

Hope this helps.

---

### Post by edunagin on 2007-05-22
I am pretty sure I did the same thing. I have tried to fix it by editing /etc/X11/xorg.conf and changing the keyboard section to a 102 keyboard instead of a 105 as listed. 

It did not help me, so I hope someone will give us a clue.

Peace..ed

---

### Post by codesplice on 2007-05-22
**edunagin**,
Do you have the correct keyboard layout selected? ("us" in xorg.conf)

Here's my keyboard section that works perfectly:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

```

---

### Post by VoidBoy on 2007-05-22
have you checked the keyboard set up?..........the one in system-preferences-keyboard,
when the window appears, select "layouts", make sure the "keyboard model" says: Generic 105-key.

The box below  needs to have "U.S. English" selected as your default

Then, you go to system-administration-language support................
if a window appears saying you need to install something, just click "remind me later"
In the other box(Language Support) make sure your default language
is "English (United States of America)"

---

### Post by Greydog on 2007-05-30
Just a thought....Make sure that you haven't pressed your "num lk" key........don't ask how I know.

u=4, i=5, etc.

boy did I feel stupid!

Greydog

---

