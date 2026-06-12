---
title: "I need to edit the Grub config file in Ubuntu"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by melfig on 2007-10-14
When i get the boot screen and i go to choose my OS i get and error but if instead i hit 'e' to edit the file and make sure that (hd1,0) is highlighted and hit 'e' again to edit this and change it to (hd0,0) hit enter and then press 'b' Ubuntu loads right up without no problem i want to make this change permanent though and i read that i have to edit the grub config file but i don't have a clue on how to do this as i am new to Ubuntu.

---

### Post by Tomosaur on 2007-10-14
> **melfig said:**
> When i get the boot screen and i go to choose my OS i get and error but if instead i hit 'e' to edit the file and make sure that (hd1,0) is highlighted and hit 'e' again to edit this and change it to (hd0,0) hit enter and then press 'b' Ubuntu loads right up without no problem i want to make this change permanent though and i read that i have to edit the grub config file but i don't have a clue on how to do this as i am new to Ubuntu.


Hit alt+f2, then type 'gksudo gedit /boot/grub/menu.lst'.

When the box pops up, enter your password and the config file will open in an editor. Simply make the changes you need, then save and close the editor.

There are various points in the file you may need to edit, I would suggest you read the following page to make sure you understand what you're doing: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

In the link in my signature is a GUI grub configurator - but it doesn't provide the functionality you need. It DOES have a 'direct edit' option, but this is really only meant for people who already know their way around the grub config file. I suggest you read the page above and then make the changes you need.

---

### Post by ramjet_1953 on 2007-10-14
There is also a GUI available for this called QGRUBEditor.

Just download and follow the install instructions here:

[http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391](http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391)

Regards,
Roger 8)

---

