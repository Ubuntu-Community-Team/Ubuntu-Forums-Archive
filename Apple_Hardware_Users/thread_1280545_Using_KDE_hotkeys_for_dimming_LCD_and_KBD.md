---
title: "Using KDE hotkeys for dimming LCD and KBD"
date: 2009-10-02
forum: Apple Hardware Users
---

### Post by MadEgg on 2009-10-02
Yesterday I succesfully installed 9.10 Karmic on my MacBook Pro 5,5. But I do have some issues with the hotkeys. Volume works fine but I cannot use the keys to increase/decrease LCD backlight of keyboard backlight.

I have installed pommed, which seems to sort of work. There are two issues with it: changing screen brightness shows the indicated on the screen but the actual brightness is not changed, and changing volume is fighting with KDE's built in hotkeys for changing the volume, resulting in unpredictable results.

The latter can possibly be resolved by remapping the KDE hotkeys. But the first one is not that easy. I found out how to manually change the LCD brightness and keyboard brightness by echoing values to the sysfs filesystem. So I wrote two small C++ programs that increase or decrease this value by a specified amount within 0 and 255. I installed them in /usr/bin and put SETUID on them to allow them to be executed with root permissions for every user. This works like a charm.

Next step was to bind hotkeys to these programs. I added 4 menu items in the K-Menu for increasing and decreasing both brightnesses. These menuitems also do what they should do.

The problem arises when I bind hotkeys to them. I can bind F-keys, letters keys etc to them no problem. But when I bind XF86MonBrightnessDown etc to them, they do not work anymore. It does capture those keys when I specify which hotkey they should react to, but when I press those buttons, the scripts are not executed.

Somehow KDE seems to blacklist those keys and does not respond to them. As a workaround I have mapped them to Ctrl+F1, Ctrl+F2, Ctrl+F5 and Ctrl+F6 which is not that big a change from Fn+F1, Fn+F2, Fn+F5 and Fn+F6 but still I think it should be possible. Any clue on how to fix this would be great!

---

### Post by MadEgg on 2009-10-07
*kick*

Or is this a more general KDE problem and should I post in another forum??

---

