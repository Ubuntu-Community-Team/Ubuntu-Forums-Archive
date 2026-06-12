---
title: "Windows Key"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by spyke01 on 2006-08-29
Is it possible to use the windows key for keyboard shortcuts? Whenever i try to use it the rogram takes me to desktop elated settings. The ones i want to mainly set are 

Windows + R = Run application
Windows + D = Minimize all windows
Windows + L = Lock computer

---

### Post by icksa on 2006-08-30
Hi:
You can use the windows key to do whatever you want using gconf-editor, but I  dont know how to use the windows key in combination with another key. To map just the windows key, use the following steps...

open a terminal (Applications->Accesories->Terminal), at the prompt, type the following command:

gconf-editor

A window should open up, on the left is a tree list. Expand the "apps" entry, then expand the "metacity" entry. Under metacity, there should be a link for "global_keybindings", click on that.

On the right of the window is a table with two columns. Double click on the "value" corresponding to run_command_1 (it should say disabled), and now you should be able to type in a new value. You can basically specify any key you want. The windows key is usually mapped to the value Super_L, type this instead of disabled.

Next, back in the tree on the left click on the keybinding_commands entry. Double click the "value" for command_1, and type the name of the program you would like to execute. For example, if you want to open a terminal when you hit the windows key, type gnome-terminal there.

Thats it, when you hit the windows key now, the program you specified should run. To my knowledge, this is the easiest way to accomplish this, maybe someone else knows better.

[Edit]
I figured out how to use the windows key with other keys (like control/alt etc...). Instead of typing "Super_L" under the run_command_1 above, you can use the value <mod4>. So, for example, to set windows key + T to open a terminal, you would change the value of run_command_1 to:

<mod4>T

To see when keys are bound to what modifiers, just open a terminal and type xmodmap.


Thanks

---

### Post by aysiu on 2006-08-30
I believe you can change it from being one key to being a modifier key you use in conjunction with other keys if you change the options in your keyboard settings.

Not sure what option to pick, though...

---

### Post by jISh on 2006-08-30
Out of curiosity, any way to make the Windows key open the USP? (Ubuntu System Panel)

---

### Post by ACGarland on 2008-04-08
This page describes one way of creating an alternative keyboard layout to get the WIN key to be mapped from Super-L to F15.

[http://www.users.bigpond.com/vkelim/SuSE_notes/node72.html](http://www.users.bigpond.com/vkelim/SuSE_notes/node72.html)

For instance, by defining a "us_win" keyboard selection which customizes "us" to change the WIN key to generate F15, then you can use the regular keyboard mapping capabilities within system configuration to assign F15 to bringing up the menu.

1. Look at the above link to get an idea how to create a custom "internationalization" for your keyboard which is a variation on your local setting (e.g., 'us', 'jp').

2. In system settings, select your new internationalization (e.g., 'us_win').

3. In system settings, keyboard and mouse, keyboard shortcuts, change the "Popup Launch Menu" to customize it and press the WIN key (which will assign F15).

4. By judicious use of menu positioning and naming, you can emulate most anything you want by having <WIN> on its own bring up the menu or <WIN> followed by some other key to immediately launch an application. For example, I have <WIN><E> launch "konqueror ~" which emulates starting explorer under windows.

---

### Post by canthus13 on 2008-04-08
It's already used for several default keybindings, such as win-E to initiate Expo in compiz.  You'll often see it referred to as Super, in which case the previously mentioned keybinding would be Super-E. (Super's not some sort of Linux elitism... It refers to a key that existed on a few models of terminals back in the early days.)

--Me

---

### Post by ACGarland on 2008-04-08
One of the problems with leaving the WIN key mapped as Super is under KDE when you try to use it as a custom key mapping it gets interpreted as "WIN+" -- like a shift key -- something that must be combined with another key.  The KDE keyboard customization won't take the <WIN+> key on its own for an assignment. Therefore, you can't type the key on its own to bring up the launch menu--which is the very thing that most folks migrating from Windoze would expect it to do.

By mapping it to F15, it is no longer treated as a combination key and can be used to bring up the menu.  My understanding is that this KDE limitation does not occur in Gnome.

After mapping it to F15, you can then use it on its own (to bring up the menu) or in combination with other keys (multi-key assignment) or in sequences (bring up the menu, then the next key chooses the application from the menu).  So more flexibility results.

If all you want is WIN+<another key> to launch applications, and don't care about using it on its own to bring up the launch menu, then there is no need to map it to F15.

---

### Post by harrybazeegar on 2008-04-08
TIP: I use Ctrl+Shift in place of Win in all these combinations... so with a little practice it will get just as easy :)

besides u can assign the windows key to open the Aplications menu...

---

