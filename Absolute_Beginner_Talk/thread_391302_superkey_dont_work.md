---
title: "superkey dont work"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by progrockusa on 2007-03-23
I'm using a custom laptop.
windows key works fine in windows xp (running a dual boot)
but in ubuntu with beryl it does not work.
any resolutions for this?

---

### Post by gradedcheese on 2007-03-23
What do you want that key to do?  You need to map it to something.  Use System->Preferences->Keyboard Shortcuts, find an action you want, and then press the key to have it mapped (for example, opening the Applications menu)

---

### Post by dfreer on 2007-03-23
A lot of Beryl functions default to using the windows key. One solution is to change the beryl defaults.

But what you probably want to do is to open 
System > Preferences > Keyboard > Layout Options
Change the *Alt/Win Key* behaviour from *Default* to *Super is mapped to the Win-Keys (Default)*

This should let you use Rain and other beryl functions

---

### Post by mcduck on 2007-03-23
> **dfreer said:**
> A lot of Beryl functions default to using the windows key. One solution is to change the beryl defaults.

But what you probably want to do is to open 
System > Preferences > Keyboard > Layout Options
Change the *Alt/Win Key* behaviour from *Default* to *Super is mapped to the Win-Keys (Default)*

This should let you use Rain and other beryl functions

Also check that you are using a keyboard layout with correct number of keys, if you have a 105-key keyboard and layout is set to 104, there will of course be a key that doesn't work (and usually that seems to be the super key).

---

### Post by Cuppa-Chino on 2007-03-24
have a similar problem with beryl

I use german keyboard and that needs right alt key to be a third level chooser.

as in my xorg.conf
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

but beryl does not recognise it. I found a work around [here]("http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#Wrong_keyboard_layout") but do not know how that works

a one off work around that seems to work is
```
echo "keycode 113 = Mode_switch" | xmodmap -

```

but how do I automate that

---

### Post by p0wd3r on 2007-06-30
Thanks for the info, changing the option of the superkey helped.  I mapped Super+1~4 to my work spaces, and Super+R to run, etc...  However, is it possible to set the superkey to launch any program?  I want to map Super+E to the File Browser application (just can't break years of windows shortcut habits :D).  What do I need to edit to make that happen?  From the System > Pref > Keyboard Shortcuts I didn't see any option for custom additions to the list.  Any suggestions would be helpful.

---

