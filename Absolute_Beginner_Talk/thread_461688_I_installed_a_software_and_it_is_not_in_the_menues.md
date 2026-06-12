---
title: "I installed a software and it is not in the menues, what should i do?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-01
Hi
thank you for reading my post
I installed a bittorrent client from [http://www.bittorrent.com/download](http://www.bittorrent.com/download) and not it is not in the menus.
I download the bed file and then package manager download some other packages as dependencies and install them.

where i should look for software that i installed.


Thanks

---

### Post by daimaru on 2007-06-01
try in terminal 
whereis nameofurprogram
eg
whereis bittorrent
should give you the location then you can add it to the panel for exmaple by right clicking it choosing add to pannel --> custom application launcher 
enter a name 
under command: enter the location of your app eg: /usr/bin/bittorrent or where ever it is 
you can even choose an icon if you got one by clicking the icon button and browsing to the file.

---

### Post by ramjet_1953 on 2007-06-01
Unfortunately, some programmers do not include placement in the menu system as a necessity.

If you re-open Synaptic and then have a look at the installed files, you will see listings in directories like[COLOR="Blue"] /usr/bin and usr/share.[/COLOR]

The executables are usually there.

You can create a menu item using System>Preferences>Main Menu tool.

Regards,
Roger :cool:

---

