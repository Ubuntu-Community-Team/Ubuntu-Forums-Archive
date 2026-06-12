---
title: "problems with the keyboard map on an acer laptop"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by tgorjanc on 2007-09-13
Hi all,

I just made the transition from XP to kubuntu on sunday and things are going surprisingly well so far :)

I've run into one annoying problem so far: my keyboard map is screwy.

The basic letters and numbers work, but some keys aren't mapped to their proper keys, for example @ is mapped to right alt-2, not shift-2

The laptop is an Acer Aspire 5610

Here is a what my keyboard section looks like in xorg.conf:

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver      "kbd"
  Option     "CoreKeyboard"
  Option     "xkbRules" "xorg"
  Option     "xkbModel" "pc105"
  Option     "xkbLayout" "us"
  Option     "xkbOptions" "lv3:ralt_switch" 
EndSection

I know that this is a laptop keyboard, so it shouldn't be a pc105, but i don't know what i should enter there.  ditto for the last line ralt_switch. I am using a US keyboard

Thanks a lot!

Tim

---

### Post by mikeyphi on 2007-09-14
In Ubuntu (don't know about Kubuntu) select System/Preferences/Keyboard and then make a selection under the layout tab. Try a few different types until you find the right one!!

---

### Post by shearn89 on 2007-09-14
You could try (after backing up xorg.conf) changing "ralt_switch" to something like "shift_switch"?

---

