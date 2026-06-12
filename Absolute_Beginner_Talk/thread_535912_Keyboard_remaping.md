---
title: "Keyboard remaping"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by SnoopDeVille on 2007-08-27
I would like to remap some keys on my keyboard..... the main ones would be from  ` to ~

and some other.... 

How can i do this folks :) ? 

Totally clueless here :P 

Thank you !

---

### Post by wormser on 2007-08-27
I believe this is what you are looking for.

System> Preference> Keyboard Shortcuts.

If you do not see the option there then right click on System> Edit Menus> System> Preferences> check the box for Keyboard Shortcuts.

---

### Post by SnoopDeVille on 2007-08-27
Its not that simple..... and no that's not what i was looking for :) 

I wish to remap my ` key (left button from key 1) ...so that when i press it it would output 

~ instead of ` 

And im still clueless how to do it

In other words, i wish that when i press it it would act as a Shift click of the same button :)

---

### Post by shearn89 on 2007-08-27
Like this (i think, this guide is written for an older version of 'buntu, so not sure how well it works):


1. Dump the keymappings to a file:
```

sudo dumpkeys --keys-only > /etc/mykeys

```

2.i   Find the keycode of the ` key:
ctrl-alt-f1 to get to real terminal (don't know why, but the command doesn't work for me unless on a real terminal).
Login, then
```

showkey -m
#press the ` key and wait for it to quit
logout

```

2.ii  Open the mykeys file, and locate the section looking something like:
```

keycode <keycode you just found> = `	something	something	something
	alt 	blah
	control	blah

```
and change the " = ` " bit to " = ~ "

3. Save the file.

4. Check it works by loading the keymaps:
```

sudo loadkeys /etc/mykeys

```

5. If it does, make it autoload (backup rc.boot first):
```

sudo gedit /etc/rc.boot
#then add to the end of it:
loadkeys /etc/mykeys

```
save and exit.

6. Reboot if you wish to check it works.

This might work, cos i got it from an old copy of "Linux Desktop Hacks", which is a bit behind the times, and not designed specifically for ubuntu. O'Reilly do another book called "Ubuntu Desktop Hacks" which looks awesome though, i might buy it...

---

