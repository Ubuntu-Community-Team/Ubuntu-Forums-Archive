---
title: "[SOLVED] Incorrect keyboard layout on macbook"
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by capawi on 2008-07-31
I'm running Ubuntu 8.04 on my Core Duo Macbook and have noticed that the keyboard layout is incorrect. In 'Keyboard Preferences' it is set to:

[IMG]http://img214.imageshack.us/img214/9568/screenshotkeyboardprefesc7.png[/IMG]

I have tried changing this to Apple>MacBook/MacBook Pro (Intl) but i get the following error:

[IMG]http://img294.imageshack.us/img294/2207/screenshotgnomesettingszf4.png[/IMG]

Any help would be greatly appreciated 

Regards 

Carl 

PS. How do I use 'hash' on this keyboard as I'm currently learning C++ but it is impossible without a hash key

---

### Post by hajk on 2008-08-01
Well, Apple would consider their keyboard layout on the MacBook correct...

You should realize that keyboard layouts specified in Xorg are always running a bit behind the times, and so it is for the keyboard of the various MacBook models. Instead of getting all worked up about this, I've found it easiest to take matters in my own hand...

I usually take the "pc104" layout (in /etc/X11/xorg.conf) as starting point (but "pc105" or somesuch would also be OK), then use the xev command in a terminal to map the various keys (install the "xev" package, if necessary). This will give you the keycodes and the correct names of the keys (such as "numbersign" for the hash mark #). Make a note of all {keycode,name} combinations that have the wrong assignment, i.e. that don't match what's printed on the key. Also, for good measure, make a note of the keycodes of the left and right Apple keys and of the lower Enter key.

Once that's done, edit a new file /usr/local/bin/keyboard to fix the keyboard. The following example is for my MacBook Pro:```

#!/bin/bash
## Keyboard modifications to run at startup
xmodmap -e "keycode 49 = section plusminus"
xmodmap -e "keycode 94 = grave asciitilde"

xmodmap -e "keycode 115 = ISO_Level3_Shift"
xmodmap -e "keycode 116 = Multi_key"
xmodmap -e "keycode 113 = Pointer_Button3"
xkbset m
```
The keycodes will be different for the MacBook, and you would have to add lines to fix the "numbersign". You may not need the last four lines that assign, respectively, the left Apple key as the third-level chooser, the right Apple key as the dead-letter key and the lower Enter key to be the right mouse click (XKBSET must also be set for keyboard control of mouse).

Once done, make this script executable by all```

sudo chmod a+x /usr/local/bin/keyboard
```and add it to the Startup programmes in the System -> Preferences -> Sessions menu. It can also be executed from the command line```

keyboard
```
Now, the above will take a few minutes, but afterwards you'll have the keyboard assignments that you want and are happy with.

Enjoy!

---

### Post by capawi on 2008-08-02
Thanks very much for the help, all is working fine now :D

---

### Post by mabovo on 2008-08-02
You could make an How To very workable on this.

My MacBook struggles to not have a brazilian macintosh keyboard and none to do with xorg or gnome keyboard definition. They are all messed.

---

