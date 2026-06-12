---
title: "Lovin' the penguin but where are the shortcuts?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Gigzaholic on 2007-06-19
Yeah so, two days ago I embarked on this journey to learn linux. Since then I've reinstalled ubuntu twice, nuked grub,  and edited grub menu.lst and xorg.conf.

All is not bad though, I've finally learned enough to get around and not be a total newbie. I've installed beryl and I'm really loving linux atm. 

I have a few question though:

-what is the shortcut to shutting down? (in windows I just pressed the windows key+U+U)
-what  is the equivalent to the windows key in linux?
-How can I access the applications, places, and systems menus by just using the keyboard?

Danke Sehr:D

---

### Post by Feba on 2007-06-19
1- I don't know if it exists. Personally, I'd install tilda, then just press F12 and shut it down through the console, if you don't want to click the shut down icon.
2- For general purpose stuff, SUPER. I don't think there's a hot key to automatically open menus, although I could be wrong again.
3-Again, I'm probably wrong, but because of the way GNOME panels work i'm not sure if you could.

---

### Post by p_quarles on 2007-06-19
You can set a number of keyboard shortcuts by going to System > Preferences > Keyboard Shortcuts. 

There's also a config file somewhere that allows you to add custom actions -- sorry, can't remember what it's called at the moment.

---

### Post by p_quarles on 2007-06-19
> **Feba said:**
> 1- I don't know if it exists. Personally, I'd install tilda, then just press F12 and shut it down through the console, if you don't want to click the shut down icon.
2- For general purpose stuff, SUPER. I don't think there's a hot key to automatically open menus, although I could be wrong again.
3-Again, I'm probably wrong, but because of the way GNOME panels work i'm not sure if you could.
Sure you can. The default key for opening the app menu is alt-F2, and you can change it to anything you like, including the Windows/Super keys.

EDIT: sorry, it's alt-F1 for the app menu

---

### Post by skymera on 2007-06-19
-what is the shortcut to shutting down? (in windows I just pressed the windows key+U+U)
-what is the equivalent to the windows key in linux?
-How can I access the applications, places, and systems menus by just using the keyboard?

1. i use command line, dont ask why:
```
 sudo shutdown -P now 
``` restart ```
 sudo shutdown -r now 
```
2. the equivalent, i havent thought of that. iknow its called the Super button.
3.i think you can, ALT+F1 Applications, ETC

---

### Post by Gigzaholic on 2007-06-19
Thanks. Also, what is the shortcut key to seeing your four dekstops as a cube?

---

### Post by skymera on 2007-06-19
ctrol+alt+ (mouse click held)

or

hold middle button whilst on desktop

---

### Post by Gigzaholic on 2007-06-19
thanks;)

---

### Post by p_quarles on 2007-06-19
Just FYI, I kinda like my setup: I have the Super-Left (i.e., left Start) button configured to open a terminal, and the Super-Right button set to open the apps menu. Those buttons have no other use in Ubuntu, and I've found those commands to be especially useful.

---

### Post by perce on 2007-06-19
> **Gigzaholic said:**
> 

-what is the shortcut to shutting down? (in windows I just pressed the windows key+U+U)



In the good old days it was ctrl-alt-del, but it is desabled, I suspect because in Windows this combination does a different thing and they didn't want to confuse some newbies, who would come on the forum and rant about Linux not being ready for whatever.

If someone knows how to enable restart through ctrl-alt-del please let me know.

> 
-what  is the equivalent to the windows key in linux?
-How can I access the applications, places, and systems menus by just using the keyboard?


For me the windows key opens the menu, and then I can browse it using he arrows. But I never use it, so I don't know more.

---

### Post by Feba on 2007-06-19
I found a guide to mapping system monitor to CTRL+ALT+DEL, I imagine you could map the same thing to shut down your system with similar results.

You can press CTRL+ALT+DOWN to film reel through your desktops, but remember you have to use compiz for these sorts of effects.
> EDIT: sorry, it's alt-F1 for the app menu


Thanks, that's nifty.

---

### Post by Tea4all on 2007-07-23
Just type ```
gconf-editor
```, go to apps, metacity, keybinding_commands.  Set command 1 to ```
gksudo shutdown -P now
```  Then go to global_keybindings and set run_command_1 to ```
<Control><Alt>Delete
```.:guitar:

---

