---
title: "3ddesktop switcher"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-10-07
I tried installing this on ubunto a while back but could never get it to work
So yesterday after eventually installing the Kubunto-desktop onto my ubunto i again tried the 3ddesktop thing and suprisingly it works on the kubunto desktop......Only trouble in having is assigning some keys to it

> Run "gconf-editor". Drill down to apps --> metacity --> global_keybindings. Find "run_command_1" and change it to your key such as "F12" or "<Control><Alt>S". Then in apps --> metacity --> keybinding_commands find "command_1" and set it to "/usr/bin/3ddesk". 


Followed those instructions before realising that they were gnome instructions and i could`nt set them anyway as the "new key" option would`nt set the above for some reason......(gnome\kde:-k )
I can run it all from the terminal but it`s a bit of a drama just for a fancy desktop switch....
Anyone know what i`d do in kde for this?????????????????tia

---

### Post by fritz_monroe on 2006-10-07
I use Gnome, but found the following about defining keyboard shortcuts in KDE on [this page]("http://www.psychocats.net/ubuntu/kdegnome").  Apparently you need to create a menu item for 3ddesktop to assign a shortcut.

```
KDE also has two places to define keyboard shortcuts, but they're both
traditional point-and-click environments.

Keyboard shortcuts for custom commands are defined within the menu editor--
so the disadvantage to KDE's approach is that you have to have a menu item
(yes--it appears in the menu) for every command you create a shortcut for.

You don't have to type out the shortcut, though--you can just press it--this
goes for both the predefined commands and the menu items. 
```

---

### Post by xpod on 2006-10-07
hey hey...as simple as that.
Im so used of using gnome too that i just followed the howto on the 3ddesktop
site for gfconf without even thinking about it.

I think theres a couple of things i still need to do to have it working in gnome or some different command but it`s all fine here now...cheers

---

